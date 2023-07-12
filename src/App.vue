<template>
  <HeaderComp />
  <HeroComp />
  <!-- <GsapComp /> -->
</template>

<script>
import HeaderComp from './components/HeaderComp.vue';
import HeroComp from './components/HeroComp.vue';
import GsapComp from './components/GsapComp.vue';

export default {
  name: "App",
  components: {
    HeaderComp,
    HeroComp,
    GsapComp
  }
}
</script>

<style></style>