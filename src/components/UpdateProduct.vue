<template>
    <div>
        <h2>Actualizar cantidad de productos</h2>
        <form @submit.prevent="updateProduct">
            <div>
                <label>Seleccionar producto:</label>
                <select v-model="selectedProductIndex">
                    <option v-for="(product, index) in products" :key="index" :value="index">
                        {{ product.name }} ({{ product.sku }})
                    </option>
                </select>
            </div>
            <div>
                <label>Nueva cantidad:</label>
                <input type="number" v-model.number="newQuantity" required min="1" />
            </div>
            <button type="submit">Actualizar cantidad</button>
        </form>
    </div>
</template>

<script>
export default {
    props: ['products'],
    data() {
        return {
            selectedProductIndex: null,
            newQuantity: 0
        };
    },
    methods: {
        updateProduct() {
            if (this.selectedProductIndex !== null) {
                const updatedProduct = { ...this.products[this.selectedProductIndex], quantity: this.newQuantity };
                this.$emit('update-product', this.selectedProductIndex, updatedProduct);
            }
            this.newQuantity = 0;
            this.selectedProductIndex = null;
        }
    }
};
</script>

