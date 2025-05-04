<template>
	<div class="card">
		<div class="card-wrapper">
			<div class="card-wrapper-number">01</div>
			<div class="card-wrapper-word">unadmitted</div>
			<button class="card-wrapper-rotate" @click="emit('rotate')">Перевернуть</button>
		</div>
	</div>
</template>

<script setup>
const emit = defineEmits({
	rotate: null,
	statusChange(status) {
		return status
	},
})
</script>

<style scoped>
.card {
	width: 250px;
	height: 376px;
	border-radius: 16px;
	box-shadow: 0px 0px 16px 0px #0000001A;
	cursor: pointer;
	transition: box-shadow 0.3s;
	padding: 28px 19px;
}

.card:hover {
	box-shadow: 10px 10px 10px 0px #0000000D;
}

.card-wrapper {
	position: relative;
	border: 1px solid var(--color-health);
	display: flex;
	align-items: center;
	justify-content: center;
	height: 100%;
	border-radius: 12px;
}

.card-wrapper-number {
	position: absolute;
	background-color: var(--color-white);
	top: -8px;
	left: 16px;
	font-size: 14px;
	line-height: 16px;
}

.card-wrapper-word {
	font-size: 18px;
	line-height: 21px;
}

.card-wrapper-rotate {
	border: none;
	background-color: var(--color-white);
	font-size: 12px;
	line-height: 1.5;
	font-weight: 700;
	letter-spacing: 2px;
	position: absolute;
	bottom: -9px;
	left: 50%;
	transform: translateX(-50%);
	cursor: pointer;
	text-transform: uppercase;
	padding: 0;
}
</style>