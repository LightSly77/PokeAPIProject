<template>
  <div id="app" class="container">
    <Header></Header>
    <Body></Body>
    <Footer></Footer>
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import Body from "./components/Body.vue";
import Footer from "./components/Footer.vue";

export default {
  name: "app",
  components: {
    Header,
    Body,
    Footer
  }
};
</script>

<style>
body {
  background: repeating-linear-gradient(
      45deg,
      rgba(4, 155, 255, 0.9),
      rgba(4, 155, 255, 0.9) 1%,
      transparent 1%,
      transparent 4%
    ),
    repeating-linear-gradient(
      -45deg,
      rgba(4, 155, 255, 0.9),
      rgba(4, 155, 255, 0.9) 1%,
      transparent 1%,
      transparent 4%
    );
}
</style>