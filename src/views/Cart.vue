<template>
    <div>
    <h1 class="text-2xl font-bold bg-gray-200 flex justify-center p-2">Your Cart</h1>

     <CartItem v-for="product in items" :key="product.id" :product="product"/>

     <CartSummaryPayment />
    </div>
</template>

<script setup>
import CartItem from "../components/cart/CartItem.vue";
import CartSummaryPayment from "../components/cart/CartSummaryPayment.vue";
import { computed } from "@vue/runtime-core";
import { useStore } from "vuex";

const store = useStore();
const items = computed(()=>{
  return store.getters.cartItems;
});
</script>
