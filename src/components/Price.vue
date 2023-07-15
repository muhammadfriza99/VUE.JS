<template>
  <span>
    {{ this.prefix + Number.parseFloat(this.value).toFixed(this.precision) }}
  </span>
</template>

<script>
export default {
  props: {
    prefix: {
      type: String,
      default: "Rp",
    },
    value: Number,
    precision: {
      type: Number,
      default: 2,
    },
  },
};
</script>
