<template>
  <Header :score="score" />
	<Button>Начать игру</Button>
	<Field />
</template>

<script setup>
import Button from "@/components/Button.vue";
import Header from "@/components/Header.vue";
import Field from "@/components/Field.vue";

import { ref } from "vue";

const score = ref(100)
</script>

<style scoped></style>
