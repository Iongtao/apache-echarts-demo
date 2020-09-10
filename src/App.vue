<template>
  <div>
    <div id="main">123,456,789</div>
    <my-charts :id="one.id" :option="one.option"></my-charts>
    <my-charts
      class="two"
      width="360"
      height="160"
      :id="two.id"
      :option="two.option"
    ></my-charts>
    <my-charts
      width="320"
      height="160"
      :id="three.id"
      :option="three.option"
      @getInstence="getInstenceThree"
    />
    <my-charts
      ref="four"
      width="320"
      height="140"
      :id="four.id"
      :option="four.option"
      @getInstence="getInstenceFour"
    />
  </div>
</template>
<script>
import myCharts from "./components/myCharts";
export default {
  components: {
    myCharts,
  },
  data() {
    const data = [20, 40, 30, 50, 20, 80];
    return {
      visible: false,
      one: {
        show: false,
        id: "one",
        option: {
          title: {
            text: "ECharts 入门示例",
          },
          grid: {
            left: 100,
            right: 100,
          },
          tooltip: {
            show: true,
          },
          xAxis: {
            show: false,
          },
          yAxis: [
            {
              data: ["衬衫", "羊毛衫", "雪纺衫", "裤子", "高跟鞋", "袜子"],
              axisLine: { show: false },
              axisTick: { show: false },
            },
            {
              data: data.sort((a, b) => a - b),
              axisLine: { show: false },
              axisTick: { show: false },
            },
          ],
          series: [
            {
              type: "bar",
              z: 1,
              data: [1, 1, 1, 1, 1, 1],
              barGap: "-100%",
              itemStyle: {
                normal: {
                  borderColor: "red",
                  borderWidth: 1,
                  color: "white",
                },
              },
            },
            {
              name: "销量",
              type: "bar",
              z: 2,
              data: data,
            },
          ],
        },
      },
      two: {
        id: "two",
        option: {
          tooltip: {
            trigger: "item",
            fontSize: 10,
            formatter: "{a} <br/>{b}: {c} ({d}%)",
          },
          grid: {
            right: "100%",
          },
          legend: {
            orient: "vertical",
            right: 0,
            bottom: '20%',
            itemWidth: 6,
            itemHeight: 6,
            icon: 'circle',
            textStyle: {
              fontSize: 12,
              color: '#397cbf'
            },
            data: ["直接访问", "邮件营销", "联盟广告", "视频广告", "搜索引擎"],
          },
          series: [
            {
              name: "访问来源",
              type: "pie",
              radius: ["50%", "70%"],
              center: ["40%", "50%"],
              avoidLabelOverlap: false,
              label: {
                show: true,
                color: "rgba(0,0,0,.5)",
                fontSize: 10,
                formatter: '{d}%'
              },
              labelLine: {
                normal: {
                  length: 14,
                  length2: 8,
                  lineStyle: {
                    color: "rgba(0,0,0, .5)",
                    type: "dotted",
                  },
                },
              },
              emphasis: {
                label: {
                  show: true,
                  fontWeight: "bold",
                },
              },
              data: [
                { value: 335, name: "直接访问", itemStyle: { color: "red" } },
                { value: 310, name: "邮件营销", itemStyle: { color: "blue" } },
                {
                  value: 234,
                  name: "联盟广告",
                  itemStyle: { color: "orange" },
                },
                {
                  value: 135,
                  name: "视频广告",
                  itemStyle: { color: "skyblue" },
                },
                { value: 1548, name: "搜索引擎", itemStyle: { color: "pink" } },
              ],
            },
          ],
        },
      },
      three: {
        id: "three",
        option: {
          title: {
            text: "人流实时流量趋势",
            textStyle: {
              fontWeight: "bold",
              color: "#66e1fc",
              fontSize: 13,
            },
            left: "3%",
            top: "10%",
          },
          legend: {
            type: "plain",
            data: ["今日", "昨日"],
            top: "20%",
            right: "10%",
            itemWidth: 12,
            itemHeight: 4,
            icon: "roundRect",
            textStyle: {
              color: "#397cbf",
              fontSize: 10,
            },
          },
          grid: {
            left: "5%",
            right: "5%",
            bottom: "20%",
          },
          tooltip: {
            trigger: "axis",
          },
          xAxis: {
            type: "category",
            boundaryGap: false,
            axisTick: {
              show: false,
            },
            axisLine: {
              lineStyle: {
                color: "#397cbf",
              },
            },
            data: [],
          },
          yAxis: {
            type: "value",
            // scale: true,
            position: "right",
            splitNumber: 3,
            axisTick: {
              show: false,
            },
            axisLine: {
              show: false,
            },
            axisLabel: {
              inside: true,
              color: "#397cbf",
            },
          },
          series: [
            {
              name: "昨日",
              data: [],
              type: "line",
              itemStyle: {
                color: "#397cbf",
              },
              // itemStyle包含了lineStyle和areaStyle
              // lineStyle: {
              //   color: '#397cbf'
              // },
              areaStyle: {
                // color: "#397cbf",
                color: {
                  type: "linear",
                  x: 0,
                  y: 0,
                  x2: 0,
                  y2: 1,
                  colorStops: [
                    {
                      offset: 0,
                      color: "rgba(46, 101, 169, .4)", // 0% 处的颜色
                    },
                    {
                      offset: 1,
                      color: "rgba(12, 105, 221, .6)", // 100% 处的颜色
                    },
                  ],
                  global: false, // 缺省为 false
                },
              },
            },
            {
              name: "今日",
              data: [],
              type: "line",
              itemStyle: {
                color: "rgba(234, 149, 30, 1)",
              },
              // itemStyle包含了lineStyle和areaStyle
              // lineStyle: {
              //   color: '#397cbf'
              // },
              areaStyle: {
                // color: "#397cbf",
                color: {
                  type: "linear",
                  x: 0,
                  y: 0,
                  x2: 0,
                  y2: 1,
                  colorStops: [
                    {
                      offset: 0,
                      color: "rgba(215, 146, 50, .4)", // 0% 处的颜色
                    },
                    {
                      offset: 1,
                      color: "rgba(230, 138, 11, .6)", // 100% 处的颜色
                    },
                  ],
                  global: false, // 缺省为 false
                },
              },
            },
          ],
          dataZoom: [
            {
              show: false,
              type: "slider",
              minValueSpan: 5,
              maxValueSpan: 5,
              zoomLock: true,
              startValue: 0,
            },
          ],
        },
      },
      four: {
        id: "four",
        option: {
          title: {
            text: "车流实时流量趋势",
            textStyle: {
              color: "#66e2fc",
              fontSize: 13,
              fontWeight: "bold",
            },
            left: "3%",
          },
          grid: {
            left: "5%",
            bottom: "10%",
          },
          tooltip: {
            trigger: "axis",
            axisPointer: {
              type: "shadow",
            },
          },
          legend: {
            type: "plain",
            data: ["今日", "昨日"],
            top: "10%",
            right: "10%",
            itemWidth: 12,
            itemHeight: 4,
            icon: "roundRect",
            textStyle: {
              color: "#397cbf",
              fontSize: 10,
            },
          },
          xAxis: {
            type: "category",
            data: [],
            boundaryGap: true,
            axisTick: {
              show: false,
            },
            axisLine: {
              lineStyle: {
                color: "#397cbf",
              },
            },
          },
          yAxis: {
            position: "right",
            splitNumber: 3,
            axisTick: {
              show: false,
            },
            axisLine: {
              show: false,
            },
            axisLabel: {
              inside: true,
              color: "#397cbf",
            },
          },
          series: [
            {
              name: "今日",
              type: "bar",
              data: [],
              itemStyle: {
                color: {
                  type: "linear",
                  x: 1,
                  y: 0,
                  x2: 0,
                  y2: 1,
                  colorStops: [
                    {
                      offset: 0,
                      color: "rgba(46, 101, 169, .8)", // 0% 处的颜色
                    },
                    {
                      offset: 1,
                      color: "rgba(12, 105, 221, 1)", // 100% 处的颜色
                    },
                  ],
                  global: false,
                },
              },
            },
            {
              name: "昨日",
              type: "bar",
              data: [],
              itemStyle: {
                color: {
                  type: "linear",
                  x: 0,
                  y: 0,
                  x2: 0,
                  y2: 1,
                  colorStops: [
                    {
                      offset: 0,
                      color: "rgba(215, 146, 50, .8)", // 0% 处的颜色
                    },
                    {
                      offset: 1,
                      color: "rgba(230, 138, 11, 1)", // 100% 处的颜色
                    },
                  ],
                  global: false, // 缺省为 false
                },
              },
            },
          ],
          dataZoom: [
            {
              show: false,
              type: "slider",
              minValueSpan: 5,
              maxValueSpan: 5,
              zoomLock: true,
              startValue: 0,
            },
          ],
        },
      },
    };
  },
  created() {
    // one
    const arr = [20, 40, 30, 50, 20, 80];
    this.one.option.series[1].data = this.formatterData(
      arr.sort((a, b) => a - b)
    );
    this.one.show = true;
    //  three
    this.three.option.xAxis.data = this.generateDate().map((v) => v.time);
    this.three.option.series[0].data = this.generateDate().map((v) => v.data);
    this.three.option.series[1].data = this.generateDate().map((v) => v.data);
    this.four.option.xAxis.data = this.generateDate().map((v) => v.time);
    this.four.option.series[0].data = this.generateDate().map((v) => v.data);
    this.four.option.series[1].data = this.generateDate().map((v) => v.data);
  },
  methods: {
    formatterData(data) {
      var color = ["#ff9500", "#02d8f9", "#027fff"];
      return data.map((v, i, arr) => {
        return {
          name: v,
          value: v / 100,
          itemStyle: {
            normal: {
              show: true,
              color: i < arr.length - 3 ? color[3] : color[arr.length - 1 - i],
              barBorderRadius: 10,
            },
          },
        };
      });
    },
    generateDate() {
      return new Array(15).fill().map((v, i, arr) => {
        return {
          time: `${9 + i < 10 ? `0${9 + i}` : 9 + i}:00`,
          data: Math.floor(Math.random() * 1000) + 500,
        };
      });
    },
    getInstenceFour(chart) {
      let interval = setInterval(() => {
        let index = this.four.option.dataZoom[0].startValue;
        const len = this.four.option.dataZoom[0].maxValueSpan + 1;
        if (len + index >= this.four.option.xAxis.data.length) {
          this.four.option.dataZoom[0].startValue = 0;
        } else {
          this.four.option.dataZoom[0].startValue += 1;
        }
        chart.setOption(this.four.option);
      }, 2000);

      this.$once("hook:beforeDestory", () => {
        clearInterval(interval);
      });
    },
    getInstenceThree(chart) {
      let interval = setInterval(() => {
        let index = this.three.option.dataZoom[0].startValue;
        const len = this.three.option.dataZoom[0].maxValueSpan + 1;
        if (len + index >= this.three.option.xAxis.data.length) {
          this.three.option.dataZoom[0].startValue = 0;
        } else {
          this.three.option.dataZoom[0].startValue += 1;
        }
        chart.setOption(this.three.option);
      }, 2000);

      this.$once("hook:beforeDestory", () => {
        clearInterval(interval);
      });
    },
  },
};
</script>

<style scoped>
#main {
  font-size: 34px;
  font-family: "aaa";
}
/* .two {
  transform: rotateX(45deg);
	transform-style:preserve-3d;
} */
</style>
