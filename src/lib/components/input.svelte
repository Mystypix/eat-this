<script lang="ts">
	export let label: string
	export let name: string
	export let value: string
	export let size: 'xs' | 'sm' | 'md' | 'lg' = 'md'
	export let required: boolean = false
</script>

<label for={name} class="label">{label}</label>
<div class="indicator">
	<!-- {#if required}
		<span class="indicator-item indicator-bottom indicator-start badge">Required</span>
	{/if} -->
	<input
		{required}
		{name}
		bind:value
		class={`input input-bordered input-${size} input-primary w-full max-w-xs`}
	/>
</div>
