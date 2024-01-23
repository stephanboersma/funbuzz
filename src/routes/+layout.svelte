<script lang="ts">
	import { FirebaseApp, PageView } from 'sveltefire';
	import { auth, firestore } from '$lib/firebase';
	import { page } from '$app/stores';
	import '@picocss/pico';
</script>

<FirebaseApp {auth} {firestore}>
	<slot />

	{#key $page.route.id}
		<PageView />
	{/key}
</FirebaseApp>
