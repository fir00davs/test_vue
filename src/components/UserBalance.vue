<template>
  <div class="balance">
    <p v-if="balance <=-1">Ошибка: Баланс равен минусу</p>
    <p v-else>Ваш баланс: {{ balance }}$</p>
  </div>
</template>

<script>
export default {
  name: "UserBalance",
  props: {
    balance: {
      type: Number,
      required: true,
      default: 300,
    },
  },
};
</script>

<style scoped>
.balance {
  max-width: 400px;
  margin: 0 auto;
  padding: 20px;
  background-color: #fff;
  border-radius: 8px;
  text-align: center;
  font-weight: 600;
}

.balance p {
  margin: 10px 0;
}
</style>