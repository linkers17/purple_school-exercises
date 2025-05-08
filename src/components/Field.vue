<template>
	<Card
		v-bind="card[0]"
		@rotate="handleRotate"
		@statusChange="handleStatusChange"
	/>
</template>

<script setup>
import Card from "@/components/Card.vue";
import { ref } from "vue";

const card = ref([{
	state: 'closed',
	status: 'pending',
	translation: 'без присмотра',
	word: 'unadmitted',
}])

const handleRotate = () => {
	card.value[0].state = 'opened'
}

function handleStatusChange(status) {
	card.value[0].status = status
}
</script>