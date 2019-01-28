<template>
  <div class="row justify-content-center">
    <div class="col-12 col-md-8 d-flex justify-content-center">
      <svg class="o-chart o-chart--invisible-height"></svg>
    </div>
  </div>
</template>

<script>
import * as d3 from "d3";
export default {};
</script>

<style lang="scss">
@import "../../../scss/main.scss";
.o-chart {
  width: calc(100% - 18px);
  height: 460px;

  @media (min-width: 992px) {
    margin-top: $spacing * 6;
    height: 520px;
  }

  &--invisible-height {
    height: 1px;
  }

  g {
    path {
      transition: all 1s;
      &:hover {
        @media (min-width: 768px) {
          transform-origin: 50% 50% 50%;
          transform: scale(0.95);
        }
      }
    }

    text {
      fill: $white;
      font-family: $category-font-family;
      font-size: 12px;
      font-weight: 300;
      text-shadow: 0 0 10px #000;
      pointer-events: none;

      @media (min-width: 768px) {
        font-size: 16px;
      }
    }
  }
}
</style>
