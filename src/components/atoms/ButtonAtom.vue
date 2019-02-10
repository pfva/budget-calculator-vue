<template>
  <button class="a-button a-button--green btn" v-on:click="fireClickEvent">
    <span class="a-button__text">Calculate</span>
  </button>
</template>

<script>
export default {
  methods: {
    fireClickEvent() {
      this.$emit("buttonClickEvent");
    }
  }
};
</script>

<style lang="scss">
.a-button {
  width: 100%;
  height: 60px;
  margin-bottom: $spacing * 4;

  @media (min-width: 768px) {
    margin-bottom: $spacing * 6;
  }

  &__text {
    color: $white;
    font-family: $heading-font-family;
    font-size: 24px;
    font-weight: 700;
    text-transform: uppercase;
    text-shadow: 0 1px 5px $dark-grey;
  }

  &--green {
    border: none;
    background-color: $green;
    box-shadow: inset 0 -4px 0 darken($green, 10%);
    transition: background-color 0.15s, box-shadow 0.15s, transform 0.15s;

    &:hover {
      background-color: darken($green, 10%);
      box-shadow: inset 0 -4px 0 darken($green, 20%);
    }

    &:focus {
      outline: none;
      background-color: $green;
      box-shadow: inset 0 -4px 0 darken($green, 10%);
    }

    &:active {
      outline: none;
      background-color: darken($green, 10%);
      box-shadow: inset 0 -4px 0 darken($green, 20%);
      transform: translateY(4px);
    }
  }
}
</style>
