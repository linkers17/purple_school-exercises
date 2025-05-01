<template>
  <span>Текущая дата: {{ dateNow }}</span>
</template>

<script setup>
const dateNow = new Intl.DateTimeFormat('ru-RU', {
  dateStyle: 'full',
}).format(new Date())
</script>

<style scoped></style>
