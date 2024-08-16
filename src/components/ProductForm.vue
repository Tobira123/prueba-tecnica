<template>
  <div>
    <h2>Agregar producto nuevo</h2>
    <form @submit.prevent="addProduct">
      <div>
        <label for="name">Nombre del producto:</label>
createApp(App).mount('#app');
<input id="name" v-model="name" required placeholder="Ingrese el nombre del producto" />
      </div>
      <div>
        <label for="sku">SKU:</label>
        <input id="sku" v-model="sku" required placeholder="Ingrese el SKU del producto" />
      </div>
      <div>
        <label for="quantity">Cantidad:</label>
        <input id="quantity" type="number" v-model.number="quantity" required min="1" />
      </div>
      <button type="submit">Agregar producto</button>
    </form>


    <div v-if="products.length > 0">
      <h3>Lista de productos agregados:</h3>
      <ul>
        <li v-for="(product, index) in products" :key="index">
          {{ product.name }} (SKU: {{ product.sku }}) - Cantidad: {{ product.quantity }}
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  props: ['products'],
  data() {
    return {
      name: '',
      sku: '',
      quantity: 0
    };
  },
  methods: {
    addProduct() {
      const newProduct = {
        name: this.name,
        sku: this.sku,
        quantity: this.quantity
      };
      
      this.$emit('add-product', newProduct);

      this.name = '';
      this.sku = '';
      this.quantity = 0;
    }
  }
};
</script>


