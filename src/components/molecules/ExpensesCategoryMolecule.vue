<template>
  <div class="m-category">
    <p class="m-category__title">{{ payload.title }}</p>
    <input
      v-on:input="emitValue"
      type="number"
      class="m-category__input m-category__input--expenses form-control text-right"
      placeholder="$"
      aria-label="Sum input"
    >
  </div>
</template>

<script>
export default {
  data() {
    return {
      payloadToReturn: {
        title: this.payload.title,
        id: this.payload.id,
        value: this.payload.value
      }
    };
  },
  props: ["payload"],
  methods: {
    emitValue(event) {
      if (event.target.value === "") {
        this.payloadToReturn.value = 0;
      } else {
        this.payloadToReturn.value = parseInt(event.target.value);
      }
      this.$emit("emittedValue", this.payloadToReturn);
    }
  }
};
</script>

<style lang="scss">
.m-category {
  display: flex;
  width: 100%;
  height: 40px;
  margin-bottom: $spacing * 2;

  &__title {
    flex: 3 1 75%;
    margin-bottom: 0;
    font-family: $category-font-family;
    font-weight: 300;
    font-size: 18px;
    line-height: 40px;
    box-shadow: inset -16px 0 0 $background-color, inset 0 -2px 0 $text-color;
  }

  &__input {
    flex: 1 1 25%;
    transform: translateY(3px);
    background-color: rgba($white, 0.85);
    border-color: $background-color;
    border-radius: 0;
    font-family: $category-font-family;
    transition: background-color, transform 0.3s;

    &:focus {
      outline: none;
      border-color: inherit;
      -webkit-box-shadow: none;
      box-shadow: none;
      transform: scale(1.05);
    }

    &::-webkit-inner-spin-button,
    &::-webkit-outer-spin-button {
      -webkit-appearance: none;
      margin: 0;
    }
  }
}
</style>
