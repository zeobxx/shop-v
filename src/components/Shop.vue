<template>
  <div class="container">
    <div class="row justify-content-center">
      <div
        class="card"
        style="width: 350px"
        v-for="item in products"
        :key="item.id"
      >
        <b-card no-body class="overflow-hidden">
          <b-row no-gutters>
            <b-col md="6">
              <b-card-img
                :src="item.imgURL"
                class="card-img-top"
                :alt="item.title"
              ></b-card-img>
            </b-col>
            <b-col md="6">
              <b-card-body>
                <b-card-text>
                  <p class="card-title" >{{ item.title }}</p>
                  <p class="card-text">KRW {{ item.price.toLocaleString() }}</p>
                  <button
                    class="btn btn-outline-primary"
                    @click="addItemToCart(item)"
                  >
                    Add to cart
                  </button>
                </b-card-text>
              </b-card-body>
            </b-col>
          </b-row>
        </b-card>
      </div>
    </div>
  </div>
</template>

<script>
import { mapActions, mapGetters } from "vuex";

export default {
  name: "Shop",
  mounted() {
    this.getProducts();
  },
  computed: {
    ...mapGetters(["products"]),
  },
  methods: {
    ...mapActions(["addItemToCart", "getProducts"]),
  },
};
</script>

<style scoped>
.card {
  padding: 10px;
  border: 10px;
  font-family: Impact, Haettenschweiler, 'Arial Narrow Bold', sans-serif;
  font-size: 20px;
  background-color: bisque;
  
}
</style>