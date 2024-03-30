<template>
  <div v-if="product !== null">
    <ProductDetails :product="product" />
  </div>
</template>

<script lang="ts" setup>
  const { id } = useRoute().params;
  definePageMeta({
    layout: "products",
  });

  const uri = "https://fakestoreapi.com/products/" + id;
  interface ProductResponse {
    title: string;
    id: number;
    price: number;
  }

  // fetch products
  const { data: product } = await useFetch<ProductResponse>(uri);
</script>

<style></style>
