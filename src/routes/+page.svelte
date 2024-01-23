<script>
	import { signOut } from 'firebase/auth';
	import ProtectedRoute from '../lib/components/ProtectedRoute.svelte';
	import { auth } from '../lib/firebase';

	async function handleSignOut() {
		await signOut(auth);
	}
</script>

<ProtectedRoute>
	<main class="container">
		<h1>Welcome to SvelteKit</h1>
		<p>Visit <a href="https://kit.svelte.dev">kit.svelte.dev</a> to read the documentation</p>
		<button on:click={handleSignOut}>Sign Out</button>
	</main>
</ProtectedRoute>
