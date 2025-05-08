<template>
	<header class="header">
		<h1 class="header-title">Запомни слово</h1>
		<Score
			:score
		/>
	</header>
</template>

<script setup>
import Score from "@/components/Score.vue";

const { score } = defineProps({
	score: Number,
})
</script>

<style scoped>
.header {
	padding: 36px 62px;
	display: flex;
	align-items: center;
	justify-content: space-between;
}

.header-title {
	font-size: 16px;
	line-height: 1.5;
	text-transform: uppercase;
	letter-spacing: 2px;
}
</style>