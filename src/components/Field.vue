<template>
	<Card
		@rotate="handleRotate"
		@statusChange="handleStatusChange"
	/>
</template>

<script setup>
import Card from "@/components/Card.vue";

const handleRotate = () => {
	console.log('handleRotate')
}

const handleStatusChange = (status) => {
	console.log('handleStatusChange', status)
}
</script>