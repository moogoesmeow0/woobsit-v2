<script>
	import { page } from '$app/state';
	let { children } = $props();
	import '../styles/fonts.css';
</script>

<div class="navbar">
	<div class="navbar-left">
		<a href="/" class="logo">moo</a>
	</div>
	<div class="navbar-right">
		<a href="/" class={page.url.pathname === '/' ? 'active' : ''}>Home</a>
		<a href="/about" class={page.url.pathname === '/about' ? 'active' : ''}>About</a>
		<a href="/projects" class={page.url.pathname === '/projects' ? 'active' : ''}>Projects</a>
		<a href="/template" class={page.url.pathname === '/template' ? 'active' : ''}>Templating</a>
	</div>
</div>

{@render children()}

<style>
	:global(body) {
		margin: 0;
	}

	.navbar {
		position: sticky;
		display: flex;
		justify-content: space-between;
		align-items: center;
		padding: 1rem 2rem;
		background-color: linen;
		border-bottom: 1px solid #000;
		z-index: 1000;
	}

	.navbar-left .logo {
		font-family: 'BoldFunnel', Arial, sans-serif;
		font-size: 1.5rem;
		font-weight: bold;
		color: #000;
		text-decoration: none;
	}

	.navbar-right {
		display: flex;
		gap: 2rem;
	}

	.navbar-right a {
		font-family: 'Dosis', Arial, sans-serif;
		color: #000;
		text-decoration: none;
		font-size: 1.1rem;
		position: relative;
		transition: transform 0.2s ease;
	}

	.navbar-right a:hover {
		transform: translateY(-2px);
	}

	.navbar-right a::after {
		content: '';
		position: absolute;
		bottom: -5px;
		left: 0;
		width: 0;
		height: 1px;
		background-color: #000;
		transition: width 0.3s ease;
	}

	.navbar-right a:hover::after {
		width: 100%;
	}

	.navbar-right a.active::after {
		width: 100%;
	}
	@media (max-width: 768px) {
		.navbar {
			flex-direction: column;
			padding: 1rem;
		}

		.navbar-left {
			margin-bottom: 1rem;
		}

		.navbar-right {
			width: 100%;
			justify-content: space-between;
			gap: 1rem;
		}
	}
</style>
