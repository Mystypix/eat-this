<script lang="ts">
	import Input from '$lib/components/input.svelte'

	let recipeName: string
	let ingredients = [{ name: '', amount: '', unit: '' }]

	const addIngredient = () => {
		ingredients = [...ingredients, { name: '', amount: '', unit: '' }]
	}

	function removeIngredient(index: number) {
		delete ingredients[index]
	}
</script>

<h1>Add recipe</h1>
<form>
	<Input label="Recipe name" name="name" bind:value={recipeName} required />
	<h3>Ingredients</h3>
	{#each ingredients as ingredient, i}
		<div>
			<Input size="sm" label="Name" name={`name-${i}`} bind:value={ingredients[i].name} required />
			<Input
				size="sm"
				label="Amount"
				name={`amount-${i}`}
				bind:value={ingredients[i].amount}
				required
			/>
			<Input size="sm" label="Unit" name={`unit-${i}`} bind:value={ingredients[i].unit} required />
			<button class="btn btn-secondary btn-sm" on:click={() => removeIngredient(i)}>Remove</button>
		</div>
	{/each}
	<button class="btn btn-secondary btn-sm" type="button" on:click={addIngredient}
		>Add ingredient</button
	>
</form>

<pre>
    {JSON.stringify(ingredients, null, 2)}
</pre>
