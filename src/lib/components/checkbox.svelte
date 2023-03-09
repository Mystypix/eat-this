<script lang="ts">
	export let label: string
	export let checked: boolean
</script>

<label class="label cursor-pointer">
	<span class="label-text">{label}</span>
	<input type="checkbox" bind:checked class="checkbox checkbox-primary" />
</label>
