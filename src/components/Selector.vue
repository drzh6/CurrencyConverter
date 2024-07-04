<template>
	<ul>
		<li
			@click="selectItem('USDT')"
			:className="current == 'USDT' ? 'active' : ''"
		>
			USDT
		</li>
		<li
			@click="selectItem('ETH')"
			:className="current == 'ETH' ? 'active' : ''"
		>
			ETH
		</li>
		<li
			@click="selectItem('BTC')"
			:className="current == 'BTC' ? 'active' : ''"
		>
			BTC
		</li>
		<li
			@click="selectItem('SOL')"
			:className="current == 'SOL' ? 'active' : ''"
		>
			SOL
		</li>
	</ul>
</template>

<style scoped>
ul {
	list-style: none;
	width: 100px;
	padding: 0;
	border-radius: 3px;
	border: 1px solid rgb(19, 19, 19);
	display: flex;
	flex-direction: column;
	margin-top: 20px;
}
li {
	background: rgb(19, 19, 19);
	color: rgb(255, 255, 255);
	padding: 10px 10px;
	border: 1px solid black;
	text-align: center;
}
li:hover,
li.active {
	background: rgb(54, 54, 54);
	cursor: pointer;
}
</style>

<script>
export default {
	data() {
		return {
			current: '',
		}
	},
	props: {
		setCrypto: {
			type: Function,
			required: true,
		},
	},
	methods: {
		selectItem(val) {
			this.setCrypto(val)
			this.current = val
		},
	},
}
</script>
