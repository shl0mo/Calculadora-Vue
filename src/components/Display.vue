<template>
	<input type="text" class="display" readonly/>
</template>

<script>
	export default {
		props: ['valor']
	}
</script>

<style>
	.display {
		grid-column: span 4;
		background-color: rgba(255, 255, 255, 0.2);
		color: white;
		display: flex;
		justify-content: flex-end;
		align-items: center;
		text-align: right;
		padding: 20px;
		font-size: 2.2em;
		overflow: hidden;
	}
</style>