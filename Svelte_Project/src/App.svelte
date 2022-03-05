<script>
	import Component from "./component.svelte"
	let user = { loggedIn: false };
	let world = 'world ' + + ' ' + (5 - 1);
	let count = 0;

	$: if (count >= 10) {
		alert('count is dangerously high!');
		count = 0;
		count -= 1;
	}
	$: if (count < 0) {
		toggle();
		count = 0;
	}

	function incrementCount() {
		count += 1;
	}

	function toggle() {
		user.loggedIn = !user.loggedIn;
	}

	let cats = [
		{ description: 'TesT ok 1', id: 'J---aiyznGQ', name: 'Keyboard Cat ➚' },
		{ description: 'Test Ok 2', id: 'z_AbfPXTKms', name: 'Maru ➚' },
		{ description: 'tEst oK 3', id: 'OUtn3pvWmpg', name: 'Henri The Existential Cat ➚' }
	];
</script>

<header><h1>Hello {world + 2}!</h1></header>
<nav>
	{#if user.loggedIn}
		<button on:click={toggle}>Log out</button>
	{:else}
		<button on:click={toggle}>Log in</button>
	{/if}
</nav>
<section>
    <article>
		<Component>
			<p>Visit the <a href="https://svelte.dev/tutorial">Svelte tutorial ➚</a> to learn how to build Svelte apps.</p>
		</Component>
		<ul>
			{#each cats as { description, id, name }, i}
				<li> {i + 1}: <a title={description} target="_blank" href="https://www.youtube.com/watch?v={id}">{name}</a></li>
			{/each}
		</ul>
		<Component>
			<button on:click={incrementCount}>
				Clicked {count} {count === 1 ? 'time' : 'times'}
			</button>
		</Component>
	</article>
	<article><img src="favicon.png"/></article>
</section>


<style>
	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	body {
  		font-family: helvetica, arial, sans-serif;
  		margin: 2em;
	}

	header {
  		position: absolute;
  		top: 0px;
  		left: 0px;
 		width: 800px;
  		height: 70px;
  		background-color: grey;
  		text-align: center;
	}

	nav {
  		position: absolute;
  		top: 120px;
  		left: 0px;
  		width: 800px;
  		height: 54px;
  		background-color: red;
	}

	section {
  		position: absolute;
  		top: 155px;
  		left: 0px;
  		width: 800px;
  		height: 800px;
  		background-color: orange;
	}

	article {
  		margin: 20px;
  		padding: 10px;
  		border: 1px black solid;
  		background-color: rgb(0, 0, 20);
	}

	aside {
  		position: absolute;
  		top: 65px;
  		left: 800px;
  		width: 200px;
  		height: 5000px;
  		background-color: green;
	}

	footer {
  		position: absolute;
  		top: 5000px;
  		left: 0px;
  		width: 1000px;
  		height: 100px;
  		background-color: blue;
	}
</style>