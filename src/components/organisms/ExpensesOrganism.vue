/**
 * This component contains a non-ideal way to nest child components.
 * It should probably be done with v-for, but this was the only 
 * approach I found to work when I needed to access each 
 * ExpensesCategoryMolecule's specific input value
 * (to be able to sum them all together and pass as prop to
 * ExpensesTotalMolecule)
 */

<template>
  <div class="row justify-content-center">
    <div class="o-income col-12 col-md-8">
      <ExpensesHeadingAtom/>
      <ExpensesCategoryMolecule v-bind:payload="payload[0]" v-on:emittedValue="sumValues"/>
      <ExpensesCategoryMolecule v-bind:payload="payload[1]" v-on:emittedValue="sumValues"/>
      <ExpensesCategoryMolecule v-bind:payload="payload[2]" v-on:emittedValue="sumValues"/>
      <ExpensesCategoryMolecule v-bind:payload="payload[3]" v-on:emittedValue="sumValues"/>
      <ExpensesCategoryMolecule v-bind:payload="payload[4]" v-on:emittedValue="sumValues"/>
      <ExpensesCategoryMolecule v-bind:payload="payload[5]" v-on:emittedValue="sumValues"/>
      <ExpensesCategoryMolecule v-bind:payload="payload[6]" v-on:emittedValue="sumValues"/>
      <ExpensesCategoryMolecule v-bind:payload="payload[7]" v-on:emittedValue="sumValues"/>
      <ExpensesCategoryMolecule v-bind:payload="payload[8]" v-on:emittedValue="sumValues"/>
      <ExpensesCategoryMolecule v-bind:payload="payload[9]" v-on:emittedValue="sumValues"/>
      <ExpensesCategoryMolecule v-bind:payload="payload[10]" v-on:emittedValue="sumValues"/>
      <ExpensesTotalMolecule v-bind:totalSum="totalValues"/>
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
      payload: [
        {
          title: "Rent/Mortgage",
          id: 0,
          value: 0
        },
        {
          title: "Electricity",
          id: 1,
          value: 0
        },
        {
          title: "Heating/Water",
          id: 2,
          value: 0
        },
        {
          title: "Food/Groceries",
          id: 3,
          value: 0
        },
        {
          title: "Insurance",
          id: 4,
          value: 0
        },
        {
          title: "Transportation",
          id: 5,
          value: 0
        },
        {
          title: "Phone and Internet",
          id: 6,
          value: 0
        },
        {
          title: "Clothing and shoes",
          id: 7,
          value: 0
        },
        {
          title: "Debt",
          id: 8,
          value: 0
        },
        {
          title: "Savings",
          id: 9,
          value: 0
        },
        {
          title: "Entertainment",
          id: 10,
          value: 0
        }
      ],
      totalValues: 0
    };
  },
  methods: {
    sumValues(payloadToReturn) {
      let correctObj = this.payload.filter(
        obj => obj.id === payloadToReturn.id
      );
      this.payload.splice(correctObj[0].id, 1, payloadToReturn);
      let summedValues = 0;
      for (let object of this.payload) {
        summedValues += object.value;
      }
      this.totalValues = summedValues;
      this.$emit("totalExpenses", [this.totalValues, this.payload]);
    }
  }
};
</script>

<style lang="scss">
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
