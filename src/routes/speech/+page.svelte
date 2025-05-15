<script>
// @ts-nocheck

	import { browser } from '$app/environment';
	import { onMount } from 'svelte';

	let recognition = null;
	let SpeechRecognizer = null;

	const onResult = (event) => {
		for (const result of event.results) {
			console.log(result[0].transcript);
		}
	};

	onMount(() => {
		if (browser) {
			SpeechRecognizer =
				window.SpeechRecognition || window.webkitSpeechRecognition;
			if (!SpeechRecognizer) {
				alert('Speech recognition not supported in this browser.');
				return;
			}
			recognition = new SpeechRecognizer();
			recognition.continuous = true;
			recognition.interimResults = true;

			recognition.addEventListener('result', onResult);
			recognition.start();
		}
	});

	function stop() {
		if (browser) {
			if (!recognition) {
				const recognition = new SpeechRecognizer();
				recognition.continuous = true;
				recognition.interimResults = true;
				recognition.addEventListener('result', onResult);
			}
			recognition.stop();
		}
	}

	function start() {
		if (browser) {
			if (!recognition) {
				SpeechRecognizer =
					window.SpeechRecognition || window.webkitSpeechRecognition;
				const recognition = new SpeechRecognizer();
				recognition.continuous = true;
				recognition.interimResults = true;
				recognition.addEventListener('result', onResult);
			}
			recognition.start();
		}
	}
</script>

<button onclick={stop}>stop </button>
<button onclick={start}>Recognize </button>
