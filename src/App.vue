<template>
  <div id="app">
    <UserBalance :balance="balance" />
    <div class="container">
      <ProfitForm @add-profit="addProfit" />
      <ExpenseForm @add-expense="addExpense" />
    </div>
    <ExpenseStatistics :profits="profits" :expenses="expenses" :categories="categories" />
  </div>
</template>

<script>
import UserBalance from "./components/UserBalance.vue";
import ProfitForm from "./components/ProfitForm.vue";
import ExpenseForm from "./components/ExpenseForm.vue";
import ExpenseStatistics from "./components/ExpenseStatistics.vue";

export default {
  name: "App",
  components: {
    UserBalance,
    ProfitForm,
    ExpenseForm,
    ExpenseStatistics,
  },
  data() {
    return {
      balance: 300,
      profits: [
      ],
      expenses: [
        { description: "Еда", amount: 1900, category: "food" },
        { description: "Покупки", amount: 400, category: "shopping" },
        { description: "Другое", amount: 65, category: "other" },
      ],
      categories: {
        food: 1900,
        shopping: 400,
        transport: 0,
        other: 65,
      },
    };
  },
  methods: {
    addProfit(profit) {
      this.profits.push(profit);
      this.updateBalance();
    },
    addExpense(expense) {
      this.expenses.push(expense);
      this.categories[expense.category] += expense.amount;
      this.updateBalance();
    },
    updateBalance() {
      const totalProfits = this.profits.reduce((sum, p) => sum + p.amount, 0);
      const totalExpenses = this.expenses.reduce((sum, e) => sum + e.amount, 0);
      this.balance = totalProfits - totalExpenses;
    },
  },
};
</script>

<style>
.container {
  display: flex;
  justify-content: center;

}

h1 {
  text-align: center;
  margin-bottom: 20px;
}

button {
  padding: 10px 20px;
  background-color: #007bff;
  color: #fff;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

button:hover {
  background-color: #0056b3;
}
@media screen and (max-width: 600px) {
  .container {
    flex-direction: column;
  }
  
}
</style>
