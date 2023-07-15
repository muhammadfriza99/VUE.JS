<template>
  <div>
    <Navbar
      :cart="cart"
      :cartQty="cartQty"
      :cartTotal="cartTotal"
      :precision="precision"
      @toggle-slide="toggleSlider"
      @delete-item="deleteItem"
    ></Navbar>
    <price-slider
      :sliderStatus="sliderStatus"
      :maximum="maximum"
      :slideState="sliderState"
    ></price-slider>
    <product-list
      :products="products"
      :maximum="maximum"
      :precision="precision"
      @add-item="addItem"
    ></product-list>
  </div>
</template>
<script>
import Navbar from "./Navbar.vue";
import ProductList from "./ProductList.vue";
import PriceSlider from "./PriceSlider.vue";

export default {
  name: "products",
  props: [
    "products",
    "maximum",
    "precision",
    "cart",
    "cartTotal",
    "cartQty",
    "sliderStatus",
    "sliderState",
  ],
  components: {
    Navbar,
    ProductList,
    PriceSlider,
  },
  methods: {
    toggleSlider: function () {
      this.$emit("toggle");
    },
    addItem: function (item) {
      this.$emit("add", item);
    },
    deleteItem: function (index) {
      this.$emit("delete", index);
    },
  },
};
</script>
