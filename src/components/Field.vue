<template>
	<div class="field">
		<Card
			v-for="card in cards"
			:key="card.id"
			v-bind="card"
			@rotate="handleRotate"
			@statusChange="handleStatusChange"
		/>
	</div>
</template>

<script setup>
import Card from "@/components/Card.vue";
import { ref } from "vue";

const cards = ref([
	{
		id: 1,
		state: 'closed',
		status: 'pending',
		translation: 'без присмотра',
		word: 'unadmitted',
	},
	{
		id: 2,
		state: 'opened',
		status: 'pending',
		translation: 'караван верблюдов',
		word: 'camel caravan',
	},
	{
		id: 3,
		state: 'opened',
		status: 'success',
		translation: 'автомобиль',
		word: 'car',
	},
	{
		id: 4,
		state: 'opened',
		status: 'failed',
		translation: 'свинец',
		word: 'lead',
	},
])

function handleRotate(id, state) {
	const findIndex = cards.value.findIndex(card => card.id === id)
	cards.value[findIndex].state = state
	if (state === 'closed')
		cards.value[findIndex].status = 'pending'
}

function handleStatusChange(id, status) {
	const findIndex = cards.value.findIndex(card => card.id === id)
	cards.value[findIndex].status = status
}
</script>

<style scoped>
.field {
	display: flex;
	flex-wrap: wrap;
	gap: 65px 105px;
}
</style>