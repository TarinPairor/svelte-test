<script>
	let counter = $state({ count: 0 });

	let listOfItems = $state({ items: Array.from({ length: 5 }, (_, i) => i) });

	function onclick() {
		// Will log `{ count: ... }` rather than `Proxy { ... }`
		console.log($state.snapshot(counter));
	}
</script>

<svelte:head>
	<title>Test</title>
	<meta name="description" content="Test page" />
</svelte:head>

<div class="text-column">
	<button onclick={() => (counter.count += 1)}>
		clicks: {counter.count}
	</button>
	<h1>Test</h1>

	<p>List of items</p>
	<ul>
		{#each listOfItems.items as item}
			<li>
				<a href="/testpage/{item}">{item}</a>
			</li>
		{/each}

		<p>
			The <a href="/">Home</a>
		</p>
	</ul>
	<button onclick={() => listOfItems.items.push(listOfItems.items.length)}> Add item </button>
	<button onclick={() => listOfItems.items.pop()}> Remove item </button>
	<button onclick={() => (listOfItems.items = Array.from({ length: 5 }, (_, i) => i))}>
		Reset list
	</button>
</div>
