<template>
  <div class="cart">
    <div v-if="!cart.length" class="alert alert-secondary" role="alert">NO ORDER!</div>
    <div
      v-if="orderPlaced"
      @click="() => this.orderPlaced=false"
      class="alert alert-success alert-dismissible fade show"
      role="alert"
    >
      Order successfully !
      <button
        type="button"
        class="close"
        data-dismiss="alert"
        aria-label="Close"
      >
        <span aria-hidden="true">&times;</span>
      </button>
    </div>
    <ul class="list-group">
      <li class="list-group-item" v-for="item in cart" :key="item.id">
        <button
          @click="removeItemFromCart(item.id)"
          type="button"
          class="close"
          data-dismiss="modal"
          aria-label="Close"
        >
          <span aria-hidden="true">&times;</span>
        </button>
        <div class="media">
          <img width="90px" :src="item.imgURL" class="mr-4" alt="item.title" />
          <div class="media-body">
            <p class="mt-2">{{ item.title }}</p>
            <button class="qty-button btn btn-sm btn-secondary" @click="reduceQty(item.id)">-</button>
            x {{ item.qty }}
            <button
              class="qty-button btn btn-sm btn-secondary"
              @click="addQty(item.id)"
            >+</button>
          </div>
        </div>
      </li>
    </ul>
    <button
      v-if="cart.length"
      @click="placeOrder"
      class="checkout-button btn btn-outline-secondary"
      :disabled="isProcessing"
    >
      <div v-if="isProcessing" class="spinner-border" role="status">
        <span class="sr-only">Loading...</span>
      </div>
      <span v-else>Purchase (KRW {{ totalPrice.toLocaleString() }})</span>
    </button>
  </div>
</template>

<script>
import { mapGetters, mapActions } from "vuex";

export default {
  name: "Cart",
  data() {
    return {
      isProcessing: false,
      orderPlaced: false
    };
  },
  computed: {
    ...mapGetters(["cart"]),
    totalPrice() {
      return this.cart.reduce((a, b) => a + b.qty * b.price, 0);
    }
  },
  methods: {
    ...mapActions(["removeItemFromCart", "addQty", "reduceQty", "emptyCart"]),
    placeOrder() {
      this.isProcessing = true;
      setTimeout(() => {
        this.isProcessing = false;
        this.orderPlaced = true;
        this.emptyCart();
      }, 1000);
    }
  }
};
</script>

<style scoped>
.media {
  width: 80%;
  text-align: left;
}

.qty-button {
  border-radius: 50%;
  width: 30px;
  background-color:rgb(57, 5, 124);
}

.checkout-button {
  margin-top: 20px;
  background-color:rgb(197, 108, 49);
  color: darkblue;
}
</style>