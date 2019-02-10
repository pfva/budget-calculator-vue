/**
 * This component contains a non-ideal way to nest child components.
 * It should probably be done with v-for, but this was the only 
 * approach I found to work when I needed to access each 
 * IncomeCategoryMolecule's specific input value
 * (to be able to sum them all together and pass as prop to IncomeTotalMolecule)
 */

<template>
  <div class="row justify-content-center">
    <div class="o-income col-12 col-md-8">
      <IncomeHeadingAtom/>
      <IncomeCategoryMolecule v-bind:payload="payload[0]" v-on:emittedValue="sumValues"/>
      <IncomeCategoryMolecule v-bind:payload="payload[1]" v-on:emittedValue="sumValues"/>
      <IncomeCategoryMolecule v-bind:payload="payload[2]" v-on:emittedValue="sumValues"/>
      <IncomeTotalMolecule v-bind:totalSum="totalValues"/>
    </div>
  </div>
</template>

<script>
import IncomeHeadingAtom from "../../components/atoms/IncomeHeadingAtom.vue";
import IncomeCategoryMolecule from "../../components/molecules/IncomeCategoryMolecule.vue";
import IncomeTotalMolecule from "../../components/molecules/IncomeTotalMolecule.vue";

export default {
  components: {
    IncomeHeadingAtom,
    IncomeCategoryMolecule,
    IncomeTotalMolecule
  },
  data() {
    return {
      payload: [
        {
          title: "Salary",
          id: 0,
          value: 0
        },
        {
          title: "Benefits",
          id: 1,
          value: 0
        },
        {
          title: "Other Income",
          id: 2,
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
      this.$emit("totalIncome", this.totalValues);
    }
  }
};
</script>

<style lang="scss">
.o-income {
  margin-bottom: $spacing * 2;
  padding: $spacing * 3;
  border-radius: $spacing / 2;

  @media (min-width: 768px) {
    margin-bottom: $spacing * 10;
    box-shadow: 0 0 8px 4px lighten($background-color, 30%),
      0 12px 8px lighten($background-color, 10%);
  }
}
</style>
