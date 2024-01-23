<script lang="ts">
	import { SignedIn, SignedOut } from 'sveltefire';
	import LoginTemplate from '../templates/LoginTemplate.svelte';
</script>

<SignedIn>
	<slot />
</SignedIn>

<SignedOut>
	<LoginTemplate />
</SignedOut>
