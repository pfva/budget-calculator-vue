<template>
  <div class="m-total">
    <p class="m-total__title">Total:</p>
    <p class="m-total__sum m-total__sum--expenses">$ {{ totalSum || 0 }}</p>
  </div>
</template>

<script>
export default {
  props: ["totalSum"]
};
</script>

<style lang="scss">
.m-total {
  display: flex;
  width: 100%;
  height: 40px;
  padding-top: $spacing;
  margin-bottom: $spacing * 4;

  &__title {
    flex: 3 1 75%;
    margin-bottom: 0;
    padding-right: $spacing * 2;
    font-family: $heading-font-family;
    text-transform: uppercase;
    font-size: 22px;
    font-weight: 700;
    line-height: 40px;
    text-align: right;

    @media (min-width: 768px) {
      font-size: 28px;
    }
  }

  &__sum {
    flex: 1 1 25%;
    margin-bottom: 0;
    padding-right: $spacing / 2;
    font-family: $category-font-family;
    font-size: 24px;
    line-height: 40px;
    text-align: right;

    @media (min-width: 768px) {
      font-size: 28px;
    }

    &--income {
      color: $green;
      text-shadow: 0 0 3px $green;
      white-space: nowrap;
    }

    &--expenses {
      color: darken($raspberry-red, 12%);
      text-shadow: 0 0 3px darken($raspberry-red, 12%);
      white-space: nowrap;
    }
  }
}
</style>
