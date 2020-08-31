<script>
	export let name;

	let count = 0;

	function handleClick() {
		count += 1;
	}

	// the `$:` means 're-run whenever these values change'
	$: doubled = count * 2;
	$: quadrupled = doubled * 2;

	let user = { loggedIn: false };

	function toggle() {
		user.loggedIn = !user.loggedIn;
	}

	let yourname = '';

	function clearInput() {
		yourname = ''
	}

	let yes = false;

</script>

<main>
	<h1>Hello {name}!</h1>
	<p>Visit the <a href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn how to build Svelte apps.</p>

	<button on:click={handleClick}>
		Clicked {count} {count === 1 ? 'time' : 'times'}
	</button>

	<br>
	
	<p>{count} * 2 = {doubled}</p>
	<p>{doubled} * 2 = {quadrupled}</p>

	<br>
	<hr>
	<br>

	{#if user.loggedIn}
		<button on:click={toggle}>
			Log out
		</button>
	{:else}
		<button on:click={toggle}>
			Log in
		</button>
	{/if}

	<br>
	<hr>
	<br>

	<input bind:value={yourname} placeholder="enter your name">
	<button on:click={clearInput}>
		Clear Imput
	</button>
	<p>Hello {yourname || 'stranger'}!</p>

	<hr>
	<br>

	<label>
		<input type=checkbox bind:checked={yes}>
		Yes! Send me regular email spam
	</label>
	
	{#if yes}
		<p>Thank you. We will bombard your inbox and sell your personal details.</p>
	{:else}
		<p>You must opt in to continue. If you're not paying, you're the product.</p>
	{/if}
	
	<button disabled={!yes}>
		Subscribe
	</button>
	

</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>