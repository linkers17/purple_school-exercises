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
import {onMounted, ref} from "vue";

const cards = ref([])

onMounted(() => {
	getWords()
})

async function getWords() {
	const res = await fetch('http://localhost:8080/api/random-words', {
		headers: {
			'Content-Type': 'application/json',
		},
	})
	if (res.status === 200) {
		cards.value = await res.json()
		cards.value = cards.value.map((card, index) => ({
			...card,
			id: index + 1,
			state: 'closed',
			status: 'pending',
		}))
	}
}

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