<template>


 <div class="bg-gray-200"> 
    <div class="flex flex-col items-center p-4 mt-3 ">
      <div class="border-2 border-gray-500 p-3 rounded bg-white">
      <h3 class="p-2 text-2xl font-bold">{{props.product.name}}</h3>
      <p class="p-2 mt-2"><b>In Cart: </b>{{props.product.quantity}}</p>
      <h5 class="p-2 mt-2"><b>Total Cost</b> : {{item_cost}}$</h5>
      <p class="bg-gray-200 border-2 border-gray-300 p-2 mt-2">{{props.product.description.substring(0,150)}}</p>
      </div>
    </div>
     </div>  



</template>

<script setup>
import { computed, onMounted } from "@vue/runtime-core";

const item_cost = computed(()=>{
    console.log("deger",props.product.price);
  return props.product.price * props.product.quantity;
});
const props = defineProps({product:Object});
</script>
