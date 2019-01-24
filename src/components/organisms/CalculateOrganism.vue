<template>
  <div class="row justify-content-center">
    <div class="col-12 col-md-8 p-4 p-md-0">
      <ButtonAtom/>
      <CalculateTextAtom/>
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
  }
};
</script>

<style lang="scss">
@import "../../../scss/main.scss";
</style>
