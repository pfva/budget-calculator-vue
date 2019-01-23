<template>
  <div class="row justify-content-center">
    <div class="o-income col-12 col-md-8">
      <ExpensesHeadingAtom/>
      <ExpensesCategoryMolecule v-bind:categories="expensesCategories"/>
      <ExpensesTotalMolecule/>
    </div>
  </div>
</template>

<script>
import ExpensesHeadingAtom from "../../components/atoms/ExpensesHeadingAtom.vue";
import ExpensesCategoryMolecule from "../../components/molecules/ExpensesCategoryMolecule.vue";
import ExpensesTotalMolecule from "../../components/molecules/ExpensesTotalMolecule.vue";

export default {
  components: {
    ExpensesHeadingAtom,
    ExpensesCategoryMolecule,
    ExpensesTotalMolecule
  },
  data() {
    return {
      expensesCategories: [
        "Rent/Mortgage",
        "Electricity",
        "Heating/Water",
        "Food/Groceries",
        "Insurance",
        "Transportation",
        "Phone and Internet",
        "Clothing and shoes",
        "Debt",
        "Savings",
        "Entertainment"
      ]
    };
  }
};
</script>

<style lang="scss">
@import "../../../scss/main.scss";
.o-expenses {
  margin-bottom: $spacing * 2;
  padding: $spacing * 3;
  border-radius: $spacing / 2;

  @media (min-width: 768px) {
    margin-bottom: $spacing * 12;
    box-shadow: 0 0 8px 4px lighten($background-color, 30%),
      0 12px 8px lighten($background-color, 10%);
  }
}
</style>
