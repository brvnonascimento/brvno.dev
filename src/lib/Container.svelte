<script lang="ts">
	export let shouldHavePadding = true;
</script>

<div class={`container ${$$props.class}`} class:padded={shouldHavePadding}>
	<slot />
</div>

<style lang="scss">
	.container {
		margin: 0 auto;
		max-width: var(--container-max-width);
		width: 100%;
	}

	.padded {
		padding: 0 var(--container-padding-x);
	}
</style>
