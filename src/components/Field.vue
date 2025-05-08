<template>
	<Card
		v-bind="card"
		@rotate="handleRotate"
		@statusChange="handleStatusChange"
	/>
</template>

<script setup>
import Card from "@/components/Card.vue";
import { ref } from "vue";

const card = ref({
	state: 'closed',
	status: 'pending',
	translation: 'без присмотра',
	word: 'unadmitted',
})

const handleRotate = () => {
	card.value.state = 'opened'
}

const handleStatusChange = (status) => {
	card.value.status = status
}
</script>