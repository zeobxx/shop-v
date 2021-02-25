<template>
  <div id="app">
    <Header />
    <div class="main">
      <div class="container">
        <div class="row">
          <div class="col-12"><Shop /></div>
        </div>
      </div>
      <div class="container">
        <div class="row">
          <div class="col-4"></div>
          <div class="col-4" style="padding-top: 10px"><Cart /></div>
          <div class="col-4"></div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Header from "./components/Header";
import Shop from "./components/Shop";
import Cart from "./components/Cart";

export default {
  name: "App",
  components: {
    Shop,
    Header,
    Cart,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color:rgb(24, 64, 196);
  background-image: url(https://pa1.narvii.com/6524/2a68d1c2248c5e14ea86c9ab42055a91cc7a041e_hq.gif);
}
</style>