<template>
  <div class="row justify-content-center">
    <div class="col-12 col-md-8">
      <h1 class="o-siteheader text-center">{{ title }}</h1>
      <p class="o-siteheader__subtext text-center">{{ subtext }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "SiteHeaderOrganism",
  data: function() {
    return {
      title: "Online Budget",
      subtext: "Create your own budget and see what you spend your money on"
    };
  }
};
</script>

<style lang="scss">
.o-siteheader {
  color: $white;
  font-family: $heading-font-family;
  font-weight: 700;
  box-shadow: 0 4px 0 $background-color;
  margin-top: $spacing * 6;
  margin-bottom: $spacing * 2;
  padding-bottom: $spacing * 2;

  @media (min-width: 768px) {
    font-size: 56px;
  }

  &__subtext {
    color: $text-color;
    font-family: $category-font-family;
    font-size: 16px;
    font-weight: 300;
    margin-bottom: $spacing * 8;

    @media (min-width: 768px) {
      font-size: 18px;
    }
  }
}

.o-header {
  height: 220px;
  background: linear-gradient(
    90deg,
    $gradient-start-blue 0%,
    $gradient-finish-blue 100%
  );
  margin-bottom: $spacing * 6;

  @media (min-width: 768px) {
    height: 260px;
    margin-bottom: $spacing * 12;
  }
}
</style>
