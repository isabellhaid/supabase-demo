<script>
	import { supabase } from '$lib/supabase';
	let promise = supabase.from('countries').select();
</script>

<div class="m-8">
	<h1 class="text-8xl my-3 text-center">Home</h1>
	<p class="text-2xl my-3 text-center">
		Exolore our world. Discover new places. Welcome to our home.
	</p>
	<h1 class="text-4xl my-2 px-3">Countries:</h1>
	{#await promise}
		<div><span class="loading loading-spinner loading-lg" /></div>
	{:then result}
		<ul class="list-disc px-6 text-1.5xl">
			{#each result.data as country}
				<li>{country.name}</li>
			{/each}
		</ul>
	{/await}
</div>
