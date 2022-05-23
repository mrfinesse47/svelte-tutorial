<script>
	let firstName = "Jimmy"
	let lastName = "Page";
	let beltColor = "black";

	$: fullName = `${firstName} ${lastName}`//reactive value
	// $: console.log(beltColor)//will run any time a value changes
	// $: console.log(fullName)

	//or you can use a code block rather than 2 $:

	$: {
		console.log(beltColor)//will run any time a value changes
		console.log(fullName)
	}

	const handleClick =()=>{
		beltColor = "orange"
	}

	const handleInput = (e)=>{
		beltColor = e.target.value;
	}
</script>

<main>
	<p style="color:{beltColor}">{fullName} - {beltColor} belt</p>
	<input type="text" bind:value={firstName}>
	<input type="text" bind:value={lastName}>
	<input type="text" bind:value={beltColor}>
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