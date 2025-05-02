<template>
	<button class="button">
		<slot />
	</button>
</template>

<script setup></script>

<style scoped>
.button {
	color: var(--color-white);
	background-color: var(--color-button-bg);
	border: none;
	padding: 16px 10px;
	font-size: 24px;
	line-height: 1.5;
	border-radius: 100px;
	min-width: 335px;
	cursor: pointer;
	transition: background-color 0.3s;
}

.button:hover {
	background-color: var(--color-button-hover-bg);
}
</style>