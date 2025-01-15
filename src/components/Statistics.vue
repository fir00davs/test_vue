<template>
  <div class="statistics">
    <h3>Статистика</h3>
    <p><b>Общая прибыль:</b> {{ totalProfits }}$</p>
    <p><b>Общие расходы:</b> {{ totalExpenses }}$</p>
    <p><b>Самая большая трата:</b> {{ biggestExpense }}</p>
  </div>
</template>

<script>
export default {
  name: "Statistics",
  props: ["profits", "expenses"],
  computed: {
    totalProfits() {
      return this.profits.reduce((sum, p) => sum + p.amount, 0);
    },
    totalExpenses() {
      return this.expenses.reduce((sum, e) => sum + e.amount, 0);
    },
    biggestExpense() {
      if (!this.expenses.length) return "Нет";
      const maxExpense = this.expenses.reduce((max, e) => (e.amount > max.amount ? e : max));
      return `${maxExpense.name} (${maxExpense.amount}$)`;
    },
  },
};
</script>

<style scoped>

</style>