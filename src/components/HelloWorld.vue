<template>
  <div class="hello">
    <div ref="mapbox" style="width:700px;height:500px"></div>
  </div>
</template>

<script>
import "echarts/map/js/china.js";
import echarts from "echarts";
import jsonp from "jsonp";

const option = {
  title: {
    text: "",
    subtext: "数据来源于新浪网"
  },
  tooltip: {
    trigger: "item",
    textStyle: {
      fontSize: 12
    }
  },
  series: [
    {
      name: "确诊人数",
      type: "map",
      mapType: "china",
      zoom: 1.2,
      label: {
        show: true, //显示省份标签
        fontSize: 10
      },
      itemStyle: {
        emphasis: {
          areaColor: "#AAAAAA"
        }
      },
      emphasis: {
        label: {
          show: true,
          fontSize: 12,
          color: "#fff"
        }
      },
      data: []
    }
  ],
  visualMap: [
    {
      type: "piecewise",
      pieces: [
        { min: 10000 },
        { min: 1000, max: 9999 },
        { min: 100, max: 999 },
        { min: 10, max: 99 },
        { min: 1, max: 9 }
      ],
      inRange: {
        color: ["RGB(255,192,177)", "RGB(156,5,5)"]
      }
    }
  ]
};

export default {
  name: "HelloWorld",
  mounted() {
    this.getData();
    this.myChart = echarts.init(this.$refs.mapbox);
    this.myChart.setOption(option);
  },
  methods: {
    getData() {
      jsonp(
        "https://interface.sina.cn/news/wap/fymap2020_data.d.json?_=1580892522427",
        {},
        (err, data) => {
          if (!err) {
            let time = data.data.times;
            let list = data.data.list.map(item => ({
              name: item.name,
              value: item.value
            }));
            option.title.text = time + "，全国疫情地图";
            option.series[0].data = list;
            this.myChart.setOption(option);
          }
        }
      );
    }
  }
};
</script>
