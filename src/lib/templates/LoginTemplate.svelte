<script lang="ts">
	import { auth } from '$lib/firebase';
	import { createUserWithEmailAndPassword, signInWithEmailAndPassword } from 'firebase/auth';

	let username = '';
	let password = '';

	async function handleLogin() {
		// Perform login logic here
		await signInWithEmailAndPassword(auth, username, password);
	}

	async function handleSignup() {
		await createUserWithEmailAndPassword(auth, username, password);
	}
</script>

<main class="container">
	<article class="grid">
		<div>
			<hgroup>
				<h1>Sign in</h1>
				<p>A minimalist layout for Login pages</p>
			</hgroup>
			<form on:submit|preventDefault>
				<input
					type="text"
					bind:value={username}
					name="login"
					placeholder="Login"
					aria-label="Login"
					autocomplete="nickname"
					required
				/>
				<input
					type="password"
					name="password"
					bind:value={password}
					placeholder="Password"
					aria-label="Password"
					autocomplete="current-password"
					required
				/>
				<fieldset>
					<label for="remember">
						<input type="checkbox" role="switch" id="remember" name="remember" />
						Remember me
					</label>
				</fieldset>
				<button class="contrast" on:click={handleLogin}>Login</button>
				<button class="secondary" on:click={handleSignup}>Register</button>
			</form>
		</div>
		<div></div>
	</article>
</main>

<style lang="scss">
	main {
		display: flex;
		flex-direction: column;
		justify-content: center;
		min-height: calc(100vh - 7rem);
		padding: 1rem 0;
	}

	article {
		padding: 0;
		overflow: hidden;
	}

	article div {
		padding: 1rem;
	}

	@media (min-width: 576px) {
		body > main {
			padding: 1.25rem 0;
		}

		article div {
			padding: 1.25rem;
		}
	}

	@media (min-width: 768px) {
		body > main {
			padding: 1.5rem 0;
		}

		article div {
			padding: 1.5rem;
		}
	}

	@media (min-width: 992px) {
		body > main {
			padding: 1.75rem 0;
		}

		article div {
			padding: 1.75rem;
		}
	}

	@media (min-width: 1200px) {
		body > main {
			padding: 2rem 0;
		}

		article div {
			padding: 2rem;
		}
	}

	/* Nav */
	summary[role='link'].secondary:is([aria-current], :hover, :active, :focus) {
		background-color: transparent;
		color: var(--secondary-hover);
	}

	/* Hero Image */
	article div:nth-of-type(2) {
		display: none;
		background-color: #374956;
		background-image: url('./img/alessio-soggetti-8jeWeKdygfk-unsplash-1000x1200.jpg');
		background-position: center;
		background-size: cover;
	}

	@media (min-width: 992px) {
		.grid > div:nth-of-type(2) {
			display: block;
		}
	}
</style>
