<template>
  <div class="row justify-content-center">
    <div class="o-income col-12 col-md-8">
      <IncomeHeadingAtom/>
    </div>
  </div>
</template>

<script>
import IncomeHeadingAtom from "../../components/atoms/IncomeHeadingAtom.vue";

export default {
  components: {
    IncomeHeadingAtom
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
