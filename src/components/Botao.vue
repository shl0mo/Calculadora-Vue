<template>
	<button class="botao" :class="{duplo, triplo, operacao }" 
	@click="$emit('onClick', label)">
		{{label}}
	</button>
</template>

<script>
	export default {
		props: {
			label: {},
			operacao: {type: Boolean},
			duplo: {type: Boolean},
			triplo: {type: Boolean}
		}
	}
</script>

<style>
	:root {
		--cor-background-botao: #f0f0f0;
		--cor-borda-botao: solid 1px #888;
	}

	.botao {
		font-size: 1.4em;
		background-color: var(--cor-background-botao);
		border: var(--cor-borda-botao);
		outline: none;
	}

	.botao:active {
		background-color: rgba(212,212,212);
	}

	.botao.duplo {
		grid-column: span 2;
	}

	.botao.triplo {
		grid-column: span 3;
	}

	.botao.operacao {
		background-color: rgb(46, 55, 169);
		color: #fff;
	}

	.operacao:active {
		background-color: rgb(66, 77, 204);
	}
</style>