<template>
  <div id="app">
    <header class="container-fluid o-header">
      <SiteHeaderOrganism/>
    </header>

    <main class="container flex-shrink-0">
      <IncomeOrganism v-on:totalIncome="addToIncome"/>
      <ExpensesOrganism v-on:totalExpenses="addToExpenses"/>
      <CalculateOrganism/>
    </main>

    <footer class="container-fluid footer o-footer">
      <FooterOrganism/>
    </footer>
  </div>
</template>

<script>
import SiteHeaderOrganism from "./components/organisms/SiteHeaderOrganism.vue";
import IncomeOrganism from "./components/organisms/IncomeOrganism.vue";
import ExpensesOrganism from "./components/organisms/ExpensesOrganism.vue";
import CalculateOrganism from "./components/organisms/CalculateOrganism.vue";
import FooterOrganism from "./components/organisms/FooterOrganism.vue";

export default {
  name: "app",
  components: {
    SiteHeaderOrganism,
    IncomeOrganism,
    ExpensesOrganism,
    CalculateOrganism,
    FooterOrganism
  },
  data() {
    return {
      income: 0,
      expenses: 0,
      incomeMinusExpenses: 0
    };
  },
  methods: {
    addToIncome(value) {
      this.income = value;
      this.calculateIncomeMinusExpenses();
    },
    addToExpenses(value) {
      this.expenses = value;
      this.calculateIncomeMinusExpenses();
    },
    calculateIncomeMinusExpenses() {
      this.incomeMinusExpenses = this.income - this.expenses;
    }
  }
};
</script>

<style lang="scss">
@import "../scss/main.scss";
</style>
