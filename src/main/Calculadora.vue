<template>
	<div class="calculadora">
		<Display :value="valor_display"/>
		<Botao label="AC" @onClick="funcao_AC" triplo/>
		<Botao label="÷" @onClick="funcao_operador" operacao/>
		<Botao label="7" @onClick="funcao_digito"/>
		<Botao label="8" @onClick="funcao_digito"/>
		<Botao label="9" @onClick="funcao_digito"/>
		<Botao label="x" @onClick="funcao_operador" operacao/>
		<Botao label="4" @onClick="funcao_digito"/>
		<Botao label="5" @onClick="funcao_digito"/>
		<Botao label="6" @onClick="funcao_digito"/>
		<Botao label="+" @onClick="funcao_operador" operacao/>
		<Botao label="1" @onClick="funcao_digito"/>
		<Botao label="2" @onClick="funcao_digito"/>
		<Botao label="3" @onClick="funcao_digito"/>
		<Botao label="-" @onClick="funcao_operador" operacao/>
		<Botao label="0" @onClick="funcao_digito" duplo/>
		<Botao label="," @onClick="funcao_digito"/>
		<Botao label="=" @onClick="funcao_operador"/>
	</div>
</template>

<script>
	import Display from "../components/Display"
	import Botao from "../components/Botao"

	export default {
		data: function () {
			return {
				valor_display: "0",
				limpa_display: false,
				operacao: null,
				valores: [0, 0],
				indice_valor_atual: 0
			}
		},
		components: { Botao, Display },
		methods: {
			funcao_AC() {
				this.valor_display = "0"
				this.limpa_display = false
				this.operacao =  null
				this.valores = [0, 0]
				this.indice_valor_atual = 0
			},
			funcao_operador(operacao) {
				console.log("Operador!")
				operacao = operacao == "÷" ? "/" : operacao
				operacao = operacao == "x" ? "*" : operacao
				console.log(operacao)
				if (this.indice_valor_atual == 0) {
					this.operacao = operacao
					this.indice_valor_atual = 1
					this.limpa_display = true
				} else {
					const igual = operacao == "="
					const operacao_atual = this.operacao
					console.log(this.indice_valor_atual)
					this.valores[0] = eval(
						`${String(this.valores[0]).replace(',','.')} ${operacao_atual} ${String(this.valores[1]).replace(',','.')}`
					)
					console.log(this.valores[0])
					this.valores[1] = 0
					this.valor_display = String(this.valores[0]).replace('.', ',')
					this.operacao = igual ? null : operacao
					this.indice_valor_atual = igual ? 0 : 1
					this.limpa_display = !igual
				}
			},
			funcao_digito(digito) {
				if (digito == "," && this.valor_display.includes(",")) {
					return
				}
				const limpa_display = this.valor_display == "0" || this.limpa_display
				const indice_valor_atual = limpa_display ? "" : this.valor_display
				const valor_display = indice_valor_atual + digito
				this.valor_display = valor_display
				this.limpa_display = false
				this.valores[this.indice_valor_atual] = valor_display
			}
		}
	}
</script>

<style>
.calculadora {
	height: 320px;
	width: 235px;
	border-radius: 5px;
	overflow: hidden;
	display: grid;
	grid-template-columns: repeat(4, 25%);
	grid-template-rows: 1fr repeat(5, 48px);
}

</style>