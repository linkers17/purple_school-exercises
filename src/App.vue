<script setup>
const dateNow = new Intl.DateTimeFormat('ru-RU', {
  dateStyle: 'full',
}).format(new Date())
</script>

<template>
  <span>Текущая дата: {{ dateNow }}</span>
</template>

<style scoped></style>
