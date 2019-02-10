<template>
  <h3 class="a-incomeheading">
    Step One: Money In
    <span>
      <i class="a-incomeheading__arrow-icon u-hovering fas fa-arrow-alt-circle-down"></i>
    </span>
  </h3>
</template>

<script>
export default {};
</script>

<style lang="scss">
.a-incomeheading {
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
    color: $green;
    margin-right: $spacing * 4;

    @media (min-width: 992px) {
      margin-right: $spacing * 8;
    }
  }
}
</style>
