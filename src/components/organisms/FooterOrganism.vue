<template>
  <div class="row justify-content-center">
    <div class="col-12 col-md-8">
      <p class="o-footer__text text-center">{{ text }}</p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      text: "This site is for personal use only. The creator of the site is not a fiduciary advisor and takes no responsibility or liability for your personal finance or any actions or events that result from use of the aforementioned site. This site contains general information about financial products and services that should not be construed as financial advice or recommendations of particular financial products or services. Use at your own discretion."
    }
  }
};
</script>

<style lang="scss">
@import "../../../scss/main.scss";
.o-footer {
  margin-top: $spacing * 8;

  &__text {
    margin-bottom: 0;
    padding: ($spacing * 4) 0;
    border-top: 2px solid $white;
    color: darken($text-color, 40%);
    font-family: $category-font-family;
    font-size: 10px;

    @media (min-width: 768px) {
      padding: $spacing * 4;
    }
  }
}
</style>
