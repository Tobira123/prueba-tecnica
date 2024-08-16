<template>
    <div>
        <h2>Resumen del almacén</h2>
        <p>Productos total: {{ totalProducts }}</p>
        <p>Cantidad total: {{ totalQuantity }}</p>
    </div>
</template>

<script>
export default {
    props: ['products'],
    computed: {
        totalProducts() {
            return this.products.length;
        },
        totalQuantity() {
            return this.products.reduce((sum, product) => sum + product.quantity, 0);
        }
    }
};
</script>
