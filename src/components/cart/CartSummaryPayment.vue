<template>
        <div class="flex justify-center border items-center border-gray-600 bg-gray-200 mt-6 p-2">
            <h3 class="text-xl font-bold mr-3">Cart Total : ${{cart_total}}</h3>

            <button class="bg-green-300 p-2 rounded text-xl ">Pay by Credit Card</button>
        </div>
</template>

<script setup>
import { computed } from "@vue/runtime-core";
import { useStore } from "vuex";

const store = useStore();
const props = defineProps({products:Object});
const cart_total = computed(()=>{
   return  store.getters.cartTotal;
});
</script>