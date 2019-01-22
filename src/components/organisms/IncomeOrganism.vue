<template>
  <div class="row justify-content-center">
    <div class="o-income col-12 col-md-8">
      <IncomeHeadingAtom/>
      <IncomeCategoryMolecule
        v-for="category in incomeCategories"
        v-bind:key="category"
        v-bind:category="category"
      />
    </div>
  </div>
</template>

<script>
import IncomeHeadingAtom from "../../components/atoms/IncomeHeadingAtom.vue";
import IncomeCategoryMolecule from "../../components/molecules/IncomeCategoryMolecule.vue";

export default {
  components: {
    IncomeHeadingAtom,
    IncomeCategoryMolecule
  },
  data: function() {
    return {
      incomeCategories: ["Salary", "Benefits", "Other Income"]
    };
  }
};
</script>

<style lang="scss">
@import "../../../scss/main.scss";
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
