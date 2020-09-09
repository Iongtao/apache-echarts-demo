<template>
  <div :id="id" :style="{ width: `${width}px`, height: `${height}px` }"></div>
</template>

<script>
import * as echarts from "echarts";
export default {
  props: {
    option: {
      type: Object,
      default: () => {},
    },
    width: {
      type: String,
      default: "600",
    },
    height: {
      type: String,
      default: "400",
    },
    id: {
      type: String,
      default: "charts",
    },
  },
  data() {
    return {};
  },
  mounted() {
    this.initCharts();
  },
  methods: {
    initCharts() {
      const mychart = echarts.init(document.getElementById(this.id));
      mychart.setOption(this.option);
      this.$emit('getInstence', mychart)
      // return mychart;
    },
  },
};
</script>

<style scoped></style>
