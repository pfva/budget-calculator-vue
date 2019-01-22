<template>
  <div id="app">
    <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <header class="container-fluid o-header">
      <SiteHeaderOrganism/>
    </header>

    <main class="container flex-shrink-0">
      <IncomeOrganism/>
      <ExpensesOrganism/>
    </main>

    <footer class="container-fluid footer o-footer">
      <FooterOrganism/>
    </footer>
  </div>
</template>

<script>
// import HelloWorld from "./components/HelloWorld.vue";
import SiteHeaderOrganism from "./components/organisms/SiteHeaderOrganism.vue";
import IncomeOrganism from "./components/organisms/IncomeOrganism.vue";
import ExpensesOrganism from "./components/organisms/ExpensesOrganism.vue";
import FooterOrganism from "./components/organisms/FooterOrganism.vue";

export default {
  name: "app",
  components: {
    // HelloWorld,
    SiteHeaderOrganism,
    IncomeOrganism,
    ExpensesOrganism,
    FooterOrganism
  }
};
</script>

<style lang="scss">
@import "../scss/main.scss";
// #app {
//   font-family: "Avenir", Helvetica, Arial, sans-serif;
//   -webkit-font-smoothing: antialiased;
//   -moz-osx-font-smoothing: grayscale;
//   text-align: center;
//   color: #2c3e50;
//   margin-top: 60px;
// }
</style>
