<template>
  <Header :score="score" />
	<main class="main">
		<Button v-if="!isStarted" @click="isStarted = !isStarted">Начать игру</Button>
		<div v-else class="main__field">
			<Field ref="fieldRef" />
			<Button @click="reset">Начать заново</Button>
		</div>
	</main>
</template>

<script setup>
import Button from "@/components/Button.vue";
import Header from "@/components/Header.vue";
import Field from "@/components/Field.vue";

import {provide, ref, useTemplateRef} from "vue";
import { scoreProvide } from "@/constants.js";

const fieldRef = useTemplateRef('fieldRef')

const score = ref(100)
provide(scoreProvide, score)

const isStarted = ref(false)

const reset = () => {
	if (fieldRef.value)
		fieldRef.value.getWords()
	score.value = 100
}
</script>

<style scoped>
.main {
	display: flex;
	align-items: center;
	justify-content: center;
	min-height: calc(100vh - 120px);
	padding: 65px;
}

.main__field {
	display: flex;
	flex-direction: column;
	gap: 100px;
	align-items: center;
}
</style>
