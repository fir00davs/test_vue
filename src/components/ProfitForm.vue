<template>
  <div class="profit-form">
    <h3>Добавить прибыль</h3>
    <input v-model="description" placeholder="Описание прибыли" />
    <input v-model.number="amount" type="number" placeholder="Сумма" />
    <button @click="submitProfit">Добавить</button>
  </div>
</template>

<script>
export default {
  name: "ProfitForm",
  data() {
    return {
      description: "",
      amount: 0,
    };
  },
  methods: {
    submitProfit() {
      if (this.amount > 0) {
        this.$emit("add-profit", { description: this.description, amount: this.amount });
        this.description = "";
        this.amount = 0;
      }
    },
  },
};
</script>

<style scoped>
.profit-form {
  max-width: 400px;
    margin: 10px ;
    padding: 20px;
    background-color: #fff;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    border-radius: 8px;
}
.profit-form:hover{
    box-shadow: 0 0 30px rgba(0, 0, 0, 0.3);
}
.profit-form h3 {
  margin-bottom: 20px;
  text-align: center;
}

.profit-form input {
  width: calc(100% - 20px);
  margin-bottom: 10px;
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 4px;
}

.profit-form button {
  width: 100%;
  padding: 10px;
  background-color: #007bff;
  color: #fff;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

.profit-form button:hover {
  background-color: #0056b3;
}
</style>