<template>
  <div class="expense-form">
    <h3>Добавить расход</h3>
    <input v-model="description" placeholder="Описание расхода" />
    <input v-model.number="amount" type="number" placeholder="Сумма" />
    <select v-model="category">
      <option value="food">Еда</option>
      <option value="shopping">Покупки</option>
      <option value="transport">Транспорт</option>
      <option value="other">Другое</option>
    </select>
    <button @click="submitExpense">Добавить</button>
  </div>
</template>

<script>
export default {
  name: "ExpenseForm",
  data() {
    return {
      description: "",
      amount: 0,
      category: "food",
    };
  },
  methods: {
    submitExpense() {
      if (this.amount > 0) {
        this.$emit("add-expense", { description: this.description, amount: this.amount, category: this.category });
        this.description = "";
        this.amount = 0;
        this.category = "food";
      }
    },
  },
};
</script>

<style scoped>
.expense-form {
  max-width: 400px;
    margin: 10px ;
    padding: 20px;
    background-color: #fff;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    border-radius: 8px;
}
.expense-form:hover {
 
    box-shadow: 0 0 30px rgba(0, 0, 0, 0.3);
}
.expense-form h3 {
  margin-bottom: 20px;
  text-align: center;
}

.expense-form input,
.expense-form select {
  width: calc(100% - 20px);
  margin-bottom: 10px;
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 4px;
}

.expense-form button {
  width: 100%;
  padding: 10px;
  background-color: #28a745;
  color: #fff;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

.expense-form button:hover {
  background-color: #218838;
}
</style>