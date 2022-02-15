<template>
    <div >
       
        <ProductDescDrawer :product="product" :active="active.product_drawer" @closeDrawer="closeProductDrawer"/>
        <div>
            <ProductSummaryCard v-for="productList in itemList" :key="productList.id" :productList="productList" 
             @viewProduct="ProductInfo"
            />
        </div>
    </div>
</template>

<script setup>
import ProductSummaryCard from '../components/products/ProductSummaryCard.vue';
import ProductDescDrawer from '../components/products/ProductDescDrawer.vue';
import {onMounted, ref} from "vue";
import items from "../assets/data/items";

const active = ref({
    product_drawer : false
});
const itemList = ref({items});
const product = ref({});
const ProductInfo = (item) => {
  product.value = item;
  active.value.product_drawer = true;
  console.log("deneme",active.value.product_drawer);
};
const closeProductDrawer = () => {
    console.log("clicked");
    active.value.product_drawer = false;
};
</script>
