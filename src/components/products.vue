<template>
  <div>
    <h3 class="text-center" v-if="productList.length > 0">List of Products</h3>
    <hr />
    <div class="row product-container">
      <app-product v-for="(product, i) in productList" :key="i">
        <img
          class="card-img-top"
          :src="product.selectedImage"
          alt="Card image cap"
        />
        <div class="card-body" align="center">
          <h5 class="card-title">{{ product.title }}</h5>
          <small> <strong>Count : </strong> {{ product.count }} </small>
          <br />
          <small> <strong>Price : </strong> {{ product.price }}</small>
          <br />
          <small>
            <strong>Total Price : </strong> {{ product.totalPrice }}
          </small>
        </div>
      </app-product>
    </div>
  </div>
</template>
<script>
import Product from "./product";
import { EventBus } from "../main";
export default {
  components: {
    appProduct: Product,
  },
  data() {
    return {
      productList: [],
    };
  },
  created() {
    EventBus.$on("addProduct", (product) => {
      if (this.productList.length < 10) {
        this.productList.push(product);
        EventBus.$emit("sendProgressBar", this.productList.length);
      } else {
        alert("You cannot add more than 10 products.");
      }
    });
  },
};
</script>