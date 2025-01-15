<template>
  <div class="expense-statistics">
    <h3>Статистика расходов</h3>
    <div>
      <p><b>Общие расходы:</b> {{ totalExpenses }}$</p>
      <p><b>Самая большая трата:</b> {{ biggestExpense }}</p>
      <ul>
        <li>Еда: {{ categories.food }}$</li>
        <li>Покупки: {{ categories.shopping }}$</li>
        <li>Транспорт: {{ categories.transport }}$</li>
        <li>Другое: {{ categories.other }}$</li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: "ExpenseStatistics",
  props: {
    expenses: {
      type: Array,
      required: true,
    },
    categories: {
      type: Object,
      required: true,
    },
  },
  computed: {
    totalExpenses() {
      return this.expenses.reduce((sum, e) => sum + e.amount, 0);
    },
    biggestExpense() {
      if (!this.expenses.length) return "Нет";
      const maxExpense = this.expenses.reduce((max, e) => (e.amount > max.amount ? e : max), this.expenses[0]);
      return `${maxExpense.description} (${maxExpense.amount}$)`;
    },
  },
};
</script>

<style scoped>
.expense-statistics {
  margin: 0 auto;
    padding: 20px;
    background-color: #fff;
    border-radius: 8px;
    text-align: center;
}

.expense-statistics h3 {
  margin-bottom: 20px;
  text-align: center;
}

.expense-statistics p {
  margin: 10px 0;
}

.expense-statistics ul {
  list-style-type: none;
  padding: 0;
}

.expense-statistics li {
  margin: 5px 0;
}
</style>