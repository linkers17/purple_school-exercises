<template>
	<div class="card">
		<div class="card-wrapper" :class="`card-wrapper_${state}`">
			<div class="card-wrapper-number">{{ number }}</div>
			<template v-if="state === 'closed'">
				<div class="card-wrapper-word">{{ word }}</div>
				<button class="card-wrapper-rotate" @click="emit('rotate', id, 'opened')">Перевернуть</button>
			</template>
			<template v-else>
				<div class="card-wrapper-word">{{ translation }}</div>
				<button v-if="isEnded" class="card-wrapper-rotate" @click="emit('rotate', id, 'closed')">Завершено</button>
				<div v-else class="card-wrapper-actions">
					<button class="card-wrapper-button-icon" @click="emit('statusChange', id, 'failed')">
						<FailedIcon />
					</button>
					<button class="card-wrapper-button-icon" @click="emit('statusChange', id, 'success')">
						<SuccessIcon />
					</button>
				</div>
				<FailedIcon v-if="status === 'failed'" class="card-wrapper-status" />
				<SuccessIcon v-if="status === 'success'" class="card-wrapper-status" />
			</template>
		</div>
	</div>
</template>

<script setup>
import {computed} from "vue";
import FailedIcon from "@/components/icons/FailedIcon.vue";
import SuccessIcon from "@/components/icons/SuccessIcon.vue";

const emit = defineEmits({
	rotate(id) {
		return id
	},
	statusChange(id, status) {
		return [id, status]
	},
})

const { id, state, status, translation, word } = defineProps({
	id: Number,
	state: String,
	status: String,
	translation: String,
	word: String,
})

const number = computed(() => {
	if (id < 10) return `0${id}`
	return `${id}`
})

const isEnded = computed(() => {
	return status === 'success' || status === 'failed'
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

.card-wrapper-actions {
	position: absolute;
	background-color: var(--color-white);
	bottom: -12px;
	left: 50%;
	transform: translateX(-50%);
	display: flex;
	gap: 32px;
}

.card-wrapper-button-icon {
	background-color: transparent;
	border: none;
	cursor: pointer;
	height: 24px;
	width: 24px;
	padding: 0;
}

.card-wrapper-status {
	background-color: var(--color-white);
	height: 36px;
	width: 36px;
	position: absolute;
	top: -18px;
	left: 50%;
	transform: translateX(-50%);
}
</style>