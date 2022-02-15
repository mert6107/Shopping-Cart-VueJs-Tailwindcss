<template>
    <div class="bg-gray-200"> 
    <div v-for="item in props.productList" :key="item.id" class="flex flex-col items-center p-4 mt-3 ">
      <div class="border-2 border-gray-500 p-3 rounded bg-white">
      <h3 class="p-2 text-2xl font-bold">{{item.name}}</h3>
      <h5 class="p-2 mt-2"><b>Price</b> : {{item.price}}$</h5>
      <p class="p-2 mt-2"><b>Category: </b>{{item.category}}</p>
      <p class="bg-gray-200 border-2 border-gray-300 p-2 mt-2">{{item.description.substring(0,150)}}</p>
      <button @click="actionProduct(item)" class="bg-green-500 border-2 border-green-600 p-2 mt-2 text-white text-xl">View Product</button>
      </div>
    </div>
     </div>  
</template>

<script setup>

const props = defineProps({productList:Array});
const emits = defineEmits(["viewProduct"]);

const actionProduct = (item) => {
  emits('viewProduct',item);
}
</script>
