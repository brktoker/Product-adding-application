<template>
  <div class="row">
    <div class="card offset-2 col-md-3">
      <div class="card-body tex-center d-flex align-items-center flex-column">
        <img
          height="128"
          class="img-responsive text-center mb-3"
          :src="
            product.selectedImage == null
              ? '/src/assets/default.png'
              : product.selectedImage
          "
        />
        <input
          ref="file"
          type="file"
          style="display: none"
          @change="onChange($event)"
          class="form-control"
        />
        <button
          class="btn btn-outline-secondary"
          type="button"
          @click="$refs.file.click()"
        >
          Add İmage
        </button>
      </div>
    </div>
    <div class="col-md-5">
      <div class="col-md-11 card">
        <div class="card-body">
          <div class="form-group">
            <label>Product Name</label>
            <input
              v-model="product.title"
              type="text"
              class="form-control"
              placeholder="Enter Product Name"
            />
          </div>
          <div class="row">
            <div class="form-group col-md-6">
              <label>Count</label>
              <input
                v-model="product.count"
                type="text"
                class="form-control"
                placeholder="Enter Count"
              />
            </div>
            <div class="form-group col-md-6">
              <label>Price</label>
              <input
                v-model="product.price"
                type="text"
                class="form-control"
                placeholder="Enter Price"
              />
            </div>
          </div>
          <button @click="addProduct" class="btn btn-outline-info btn-block">
            Ekle!
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { EventBus } from "../main";

export default {
  data() {
    return {
      product: {
        selectedImage: null,
        title: null,
        count: null,
        price: null,
        totalPrice: null,
      },
    };
  },
  methods: {
    onChange(e) {
      const file = e.target.files[0];
      this.product.selectedImage = URL.createObjectURL(file);
    },
    addProduct() {
      this.product.totalPrice = this.product.count * this.product.price;
      EventBus.$emit("addProduct", this.product);
      this.product = {
        selectedImage: null,
        title: null,
        count: null,
        price: null,
        totalPrice: null,
      };
    },
  },
};
</script>