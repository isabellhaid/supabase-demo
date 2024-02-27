<script>
	import { supabase } from '$lib/supabase';
	let promise = supabase.from('countries').select();
</script>

<h1>Aufgaben:</h1>
<ul>
	<li>
		anstatt eines JS-Objekts, das auf der Seite dargestellt wird, möchte ich eine Liste aller Länder
	</li>
	<li>loading symbol</li>
	<li>Vercel</li>
</ul>
{#await promise}
	<div><span class="loading loading-spinner loading-lg" /></div>
{:then result}
	<ul>
		{#each result.data as country}
			<li>{country.name}</li>
		{/each}
	</ul>
{/await}
