<template>
  <transition-group
    name="fade"
    tag="div"
    @beforeEnter="before"
    @enter="enter"
    @leave="leave"
  >
    <div
      class="row mb-3 mt-3 align-items-center"
      v-for="(item, index) in showItem"
      :key="item.id"
      :data-index="index"
    >
      <div class="col-1 m-auto">
        <button class="btn btn-info" @click="$emit('add-item', item)">+</button>
      </div>
      <div class="col-sm-4">
        <img :src="item.image" class="img-thumbnail" :alt="item.name" />
      </div>
      <div class="col">
        <h1 class="text-info fw-bold">{{ item.name }}</h1>
        <p class="mb-0">{{ item.description }}</p>
        <div class="h5 float-right">
          <price :value="Number(item.price)" :precision="precision"></price>
        </div>
      </div>
    </div>
  </transition-group>
</template>

<script>
import Price from "./Price.vue";

export default {
  name: "product-list",
  components: {
    Price,
  },
  props: ["products", "maximum", "precision"],
  computed: {
    showItem: function () {
      let max = this.maximum;
      return this.products.filter(function (item) {
        return Number(item.price) <= max;
      });
    },
  },
  methods: {
    before: function (el) {
      el.className = "d-none";
    },
    enter: function (el) {
      let delay = el.dataset.index * 100;
      setTimeout(function () {
        el.className =
          "row d-flex mb-3 mt-3 align-items-center animated fadeInRight";
      }, delay);
    },
    leave: function (el) {
      let delay = el.dataset.index * 100;
      setTimeout(function () {
        el.className = "row d-flex mb-3 mt-3 align-items-center animated hinge";
      }, delay);
    },
  },
};
</script>
