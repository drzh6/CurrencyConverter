<template>
	<input
		type="number"
		min="0"
		@input="changeAmount($event.target.value)"
		placeholder="Введите число"
	/>
	<br />
	<button @click="convert()">Конвертировать</button>
</template>
<style scoped>
input {
	border-radius: 5px;
	border: 0;
	padding: 10px 5px;
	background-color: white;
	color: rgb(19, 19, 19);
	outline: none;
	margin-top: 20px;
	width: 230px;
	font-size: 1.1em;
	font-family: 'Segoe UI', sans-serif;
}
input[type='number']::-webkit-outer-spin-button,
input[type='number']::-webkit-inner-spin-button {
	-webkit-appearance: none;
}
button {
	border: 0;
	border-radius: 5px;
	padding: 8px;
	font-family: 'Segoe UI', sans-serif;
	cursor: pointer;
}
button:hover {
	transform: scale(1.03);
}
</style>
<script>
export default {
	props: {
		changeAmount: {
			type: Function,
			required: true,
		},
		convert: {
			type: Function,
			required: true,
		},
	},
}
</script>
