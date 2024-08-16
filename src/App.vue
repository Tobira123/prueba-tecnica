<template>
  <div id="app">
    <div class="section-container">
      <ProductForm @add-product="addProduct" :products="products" />
    </div>
    <div class="section-container">
      <UpdateProduct :products="products" @update-product="handleProductUpdate" />
    </div>
    <div class="section-container">
      <WarehouseSummary :products="products" />
    </div>
  </div>
</template>

<script>
import ProductForm from './components/ProductForm.vue';
import UpdateProduct from './components/UpdateProduct.vue';
import WarehouseSummary from './components/WarehouseSummary.vue';

export default {
  components: {
    ProductForm,
    UpdateProduct,
    WarehouseSummary
  },
  data() {
    return {
      products: [] // Aquí almacenaremos la lista de productos
    };
  },
  methods: {
  addProduct(newProduct) {
    this.products.push(newProduct);
  },
  handleProductUpdate(index, updatedProduct) {
    // Sumar la nueva cantidad a la cantidad existente
    this.products[index].quantity += updatedProduct.quantity;
  }
}

};
</script>

