<template>
  <h3 class="a-expensesheading">
    Step Two: Money Out
    <span>
      <i class="a-expensesheading__arrow-icon fas fa-arrow-alt-circle-down"></i>
    </span>
  </h3>
</template>

<script>
export default {};
</script>

<style lang="scss">
.a-expensesheading {
  display: flex;
  justify-content: space-between;
  color: $white;
  font-family: $heading-font-family;
  font-size: 28px;
  margin-bottom: $spacing * 2;

  @media (min-width: 768px) {
    font-size: 32px;
  }

  &__arrow-icon {
    color: darken($raspberry-red, 12%);
    margin-right: $spacing * 4;

    @media (min-width: 992px) {
      margin-right: $spacing * 8;
    }
  }
}
</style>
