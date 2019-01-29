<template>
  <div class="row justify-content-center">
    <div class="col-12 col-md-8 p-4 p-md-0">
      <ButtonAtom v-on:buttonClickEvent="handleClickEvent"/>
      <CalculateTextAtom
        v-bind:sum="sum"
        v-bind:class="{'u-hidden': isHidden, 'u-fadein': fadeIn}"
      />
    </div>
  </div>
</template>

<script>
import ButtonAtom from "../../components/atoms/ButtonAtom.vue";
import CalculateTextAtom from "../../components/atoms/CalculateTextAtom.vue";

export default {
  components: {
    ButtonAtom,
    CalculateTextAtom
  },
  data() {
    return {
      isHidden: true,
      fadeIn: false
    };
  },
  props: ["sum"],
  methods: {
    handleClickEvent() {
      this.removeHidden();
      this.fireClickEvent();
    },
    removeHidden() {
      this.isHidden = false;
      this.fadeIn = true;

      window.setTimeout(function() {
        window.scrollBy({
          left: 0,
          top: 450,
          behavior: "smooth"
        });
      }, 200);
    },
    fireClickEvent() {
      this.$emit("clickEvent");
    }
  }
};
</script>

<style lang="scss">
@import "../../../scss/main.scss";
</style>
