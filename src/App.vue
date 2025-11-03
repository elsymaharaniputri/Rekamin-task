<template>
  <div id="app">
    <NavbarMenu />
    <HeroSection />
    <div class="container-fluid">

      <CardContoh />
      <CardList />
    </div>

  </div>
</template>

<script>
import CardContoh from "./components/CardContoh.vue";
import CardList from "./components/CardList.vue";
import HeroSection from "./components/HeroSection.vue";
import NavbarMenu from "./components/NavbarMenu.vue";

export default {
  name: "App",
  components: { NavbarMenu, HeroSection, CardContoh, CardList },
};
</script>

<style>
#app {
  background-color: #E8E8E8;
}

.container-fluid {
  background-color: #D6D6D6;
}
</style>
