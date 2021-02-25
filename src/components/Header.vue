<template>
  <header>
    <div class="container">
      <nav class="navbar navbar-Blue">
        <span class="navbar-brand mb-3 h1" style="padding-top: 30px"
          >Light Stick</span
        >
        <span class="navbar-brand mb-3 h1" style="padding-top: 30px">
          Cart <span class="badge badge-primary">{{ totalQty }}</span>
        </span>
      </nav>
    </div>
  </header>
</template>

<script>
import { mapGetters } from "vuex";

export default {
  name: "Header",
  computed: {
    ...mapGetters(["cart"]),
    totalQty() {
      return this.cart.reduce((a, b) => a + b.qty, 0);
    },
  },
};
</script>

<style scoped>
header {
  margin-bottom: 10vh;
  background-color: rgb(175, 207, 226);
  font-family: Impact, Haettenschweiler, 'Arial Narrow Bold', sans-serif;
  background-image: url(http://www.over-educated.com/wp-content/uploads/2015/11/Dahlia-background-header-2217a.jpg);
}
</style>