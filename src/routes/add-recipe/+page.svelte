<script lang="ts">
	import Checkbox from '$lib/components/checkbox.svelte'
	import Input from '$lib/components/input.svelte'

	let recipeName: string
	let isPublic: boolean = false
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
			<Checkbox label="Make recipe public" bind:checked={isPublic} />
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
    {JSON.stringify(recipeName, null, 2)}
    {JSON.stringify(isPublic, null, 2)}
    {JSON.stringify(ingredients, null, 2)}
</pre>
