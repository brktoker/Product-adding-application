<template>
  <div class="container">
    <h1 class="text-center">Product adding application</h1>
    <hr>
      <app-add-product></app-add-product>
    <br><br>
    <app-progress></app-progress>
    <br><br>
    <h3 class="text-center">List of Products</h3>
    <hr>
    <app-products></app-products>
  </div>
</template>

<script>
  import AddProduct from './components/addProduct';
  import Progress from './components/progress';
  import Products from './components/products';

  export default {
    components:{
      appAddProduct : AddProduct,
      appProgress : Progress,
      appProducts : Products
    },
    data() {
      return {
        imageList: [],
        product : {
            selectedImage: null
        }
      }
    },
    
  }
</script>

<style>
  body {
    background-color: aliceblue;
    padding-top: 20px;
    padding-bottom: 20px;
  }

  .card{
    margin-right: 5px;
    margin-bottom: 5px;
  }

  .card:last-child{
    margin-right: 0px;
  }

  .col-md-2{
    max-width: 15.666667%!important;
  }

  .product-container{
    margin-left: 15px;
  }

</style>

