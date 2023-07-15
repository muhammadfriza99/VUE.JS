<template>
  <transition
    name="custom"
    enter-active-class="animated fadeInDown"
    leave-active-class="animated hinge"
  >
    <div v-if="this.sliderStatus">
      <div class="align-items-center" :class="sliderState">
        <label class="font-weight-bold mr-2">Max Price</label>
        <input
          type="number"
          class="form-control mx-2"
          style="width: 80px; text-aligm: center"
          v-model="maxAmount"
          @change="$parent.$emit('update:maximum', maxAmount)"
        />
        <input
          type="range"
          class=""
          min="0"
          max="200"
          v-model="maxAmount"
          @change="$parent.$emit('update:maximum', maxAmount)"
        />
      </div>
    </div>
  </transition>
</template>

<script>
export default {
  name: "price-slider",
  data: function () {
    return {
      maxAmount: 90,
    };
  },
  props: ["sliderStatus", "maximum", "sliderState"],
};
</script>

<style>
.fade-enter-active,
.fade-leave-active {
  transition: all 1s ease;
}

.fade-enter,
.fade-leave-to {
  opacity: 0;
}
</style>
