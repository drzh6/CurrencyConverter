<template>
	<div class="wrapper">
		<h1>Crypto</h1>
		<Input :changeAmount="changeAmount" :convert="convert" />
		<p v-if="error != ''">{{ error }}</p>
		<p class="result" v-if="result != 0">
			{{ amount }} {{ cryptoFirst }} = {{ result }} {{ cryptoSecond }}
		</p>
		<div class="selectors">
			<Selector :setCrypto="setCryptoFirst" />
			<Selector :setCrypto="setCryptoSecond" />
		</div>
	</div>
</template>

<style scoped></style>

<script>
import Input from './components/Input.vue'
import Selector from './components/Selector.vue'
import CryptoConvert from 'crypto-convert'
const convert = new CryptoConvert()

export default {
	components: { Input, Selector },
	data() {
		return {
			amount: 0,
			result: 0,
			cryptoFirst: '',
			cryptoSecond: '',
			error: '',
		}
	},
	methods: {
		changeAmount(val) {
			this.amount = val
		},
		setCryptoFirst(val) {
			this.cryptoFirst = val
		},
		setCryptoSecond(val) {
			this.cryptoSecond = val
		},
		async convert() {
			if (this.mount <= 0) {
				this.error = 'Число не может быть меньше ноля'
				return
			} else if (this.cryptoFirst == '' || this.cryptoSecond == '') {
				this.error = 'Выберите валюту'
				return
			} else if (this.cryptoFirst == this.cryptoSecond) {
				this.error = 'Вы выбрали одну и ту же валюту'
				return
			}
			this.error = ''
			await convert.ready()

			if (this.cryptoFirst == 'BTC' && this.cryptoSecond == 'ETH') {
				this.result = convert.BTC.ETH(this.amount)
			} else if (this.cryptoFirst == 'BTC' && this.cryptoSecond == 'USDT') {
				this.result = convert.BTC.USD(this.amount)
			} else if (this.cryptoFirst == 'BTC' && this.cryptoSecond == 'SOL') {
				this.result = convert.BTC.SOL(this.amount)
			} else if (this.cryptoFirst == 'ETH' && this.cryptoSecond == 'SOL') {
				this.result = convert.ETH.SOL(this.amount)
			} else if (this.cryptoFirst == 'ETH' && this.cryptoSecond == 'BTC') {
				this.result = convert.ETH.BTC(this.amount)
			} else if (this.cryptoFirst == 'ETH' && this.cryptoSecond == 'USDT') {
				this.result = convert.ETH.USD(this.amount)
			} else if (this.cryptoFirst == 'USDT' && this.cryptoSecond == 'ETH') {
				this.result = convert.USD.ETH(this.amount)
			} else if (this.cryptoFirst == 'USDT' && this.cryptoSecond == 'SOL') {
				this.result = convert.USD.SOL(this.amount)
			} else if (this.cryptoFirst == 'USDT' && this.cryptoSecond == 'BTC') {
				this.result = convert.USD.BTC(this.amount)
			} else if (this.cryptoFirst == 'SOL' && this.cryptoSecond == 'ETH') {
				this.result = convert.SOL.ETH(this.amount)
			} else if (this.cryptoFirst == 'SOL' && this.cryptoSecond == 'BTC') {
				this.result = convert.SOL.BTC(this.amount)
			} else if (this.cryptoFirst == 'SOL' && this.cryptoSecond == 'USDT') {
				this.result = convert.SOL.USD(this.amount)
			}
		},
	},
}
</script>
