<template>
    <div v-if="props.active" @click="action" />
   
    <div v-if="props.active" class="bg-white flex flex-col items-center h-[800px] w-1/2 rounded absolute drop-shadow-2xl px-5">
        <div class="ml-96 mt-4 border border-black p-1 rounded ">
            <button type="button" @click="action" >X</button> 
            
        </div>

        <div v-if="props.product" class="flex flex-col items-center">
            <h3 class="text-xl font-bold text-gray-600">{{props.product.name}}</h3>
            <p class="mt-20">{{props.product.description}}</p>
            <h3 class="text-xl mt-5 text-gray-600"><b>Price : </b>${{props.product.price}}</h3>

            <!-- Total Products -->
            <div v-if="product_total">
                <h3 class="text-center text-xl text-gray-600 mt-10">In Cart</h3>
                <h4 class="text-center text-xl text-gray-600 mt-4">{{product_total}}</h4>
               
            </div>
            <div class="mt-6 flex ">
               <button @click="removeFromCart" class="bg-red-300 p-2 mr-2 rounded text-sm">Remove</button>
               <button @click="addToCart" class="bg-green-300 p-2 rounded text-sm " >Add</button>
            </div>
        </div>
    </div>
</template>

<script setup>
import { ref } from "@vue/reactivity";
import { computed, onMounted } from "@vue/runtime-core";
import {useStore} from "vuex";

const store = useStore();
const props = defineProps({product:Object,active:Boolean});
const emits = defineEmits(["closeDrawer"]);
const addToCart = () =>{
  store.commit('addToCart',props.product);
};
const removeFromCart = () => {
   store.commit('removeFromCart',props.product);
};
const product_total = computed(() => {
   return store.getters.productQuantity(props.product);
});
const action = () => {
    emits('closeDrawer');
};


</script>
