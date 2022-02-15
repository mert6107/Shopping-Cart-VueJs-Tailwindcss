<template>
 <div>
 <router-link class="p-2 rounded ml-4 mr-3 " to="/" active-class="active" >Home</router-link>
 <router-link class="p-2 rounded ml-4 mr-3 " to="/cart" active-class="active">Cart</router-link>
  
 </div> 
 <router-view />
</template>

<script setup>
import { onMounted } from "@vue/runtime-core";
import { useStore } from "vuex";

const store = useStore();
const mount = onMounted(()=>{
  store.commit('updateCartFromLocalStorage');
});
</script>
