<template>
  <div>
    <div v-if="sum >= 0" class="a-calculatetext a-calculatetext-positive">
      <p class="a-calculatetext__main">
        You have
        <span class="a-calculatetext__main--sum-positive">$ {{ sum }}</span> left each month
      </p>
      <p class="a-calculatetext__subtext">
        Good job, keep it up!
        <span class="a-calculatetext__subtext--emoji">🎉</span>
      </p>
      <p
        class="a-calculatetext__chart-intro"
      >Here's how your different expenses compare to each other:</p>
    </div>
    <div v-else class="a-calculatetext a-calculatetext-negative">
      <p class="a-calculatetext__main">
        You're spending
        <span class="a-calculatetext__main--sum-negative">$ {{ sum }}</span> more than you earn each month
      </p>
      <p class="a-calculatetext__subtext">
        Try to lower your expenses!
        <span class="a-calculatetext__subtext--emoji">💸</span>
      </p>
      <p
        class="a-calculatetext__chart-intro"
      >Here's how your different expenses compare to each other:</p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {};
  },
  props: ["sum"]
};
</script>

<style lang="scss">
.a-calculatetext {
  font-family: $category-font-family;

  &__main {
    font-size: 24px;
    font-weight: 300;
    text-align: center;
    margin-bottom: $spacing;

    &--sum-positive {
      color: $green;
      font-weight: 400;
      text-shadow: 0 0 3px $green;
      margin-right: $spacing;
      margin-left: $spacing;
      white-space: nowrap;

      @media (min-width: 768px) {
        font-size: 28px;
      }
    }

    &--sum-negative {
      color: darken($raspberry-red, 12%);
      font-weight: 400;
      text-shadow: 0 0 3px darken($raspberry-red, 12%);
      margin-right: $spacing;
      margin-left: $spacing;
      white-space: nowrap;

      @media (min-width: 768px) {
        font-size: 28px;
      }
    }
  }

  &__subtext {
    font-size: 18px;
    font-weight: 300;
    text-align: center;
    margin-bottom: $spacing * 3;

    &--emoji {
      font-size: 28px;
      padding-left: $spacing;
    }
  }

  &__chart-intro {
    font-size: 14px;
    font-weight: 300;
    text-align: center;
  }
}
</style>
