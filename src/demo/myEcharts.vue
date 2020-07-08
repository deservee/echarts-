<template>
  <div class="centers">
    <div id="bar1">
      <!-- 为 ECharts 准备一个具备大小（宽高）的 DOM -->
      <div id="main1" style="float:left;width:100%;height: 180px"></div>
    </div>
    <div id="bar2">
      <div id="main2" style="float:left;width:100%;height: 180px"></div>
    </div>
    <div id="bar3">
      <div id="main3" style="float:left;width:100%;height: 180px"></div>
    </div>
  </div>
</template>
 
<script>
var echarts = require("echarts");

export default {
  data() {
    return {
      // 数据
      data: [],
      data1: [],
      data2: []
    };
  },
  mounted() {
    this.initData();
    this.initData1();
    this.initData2();
  },
  methods: {
    //初始化数据
    initData() {
      var myChart = echarts.init(document.getElementById("main1"));
      window.onresize = myChart.resize;
      // 绘制图表
      myChart.setOption({
         angleAxis: {
        max: 2,
        startAngle: 30,
        splitLine: {
            show: false
        }
    },
     title: {
          textStyle: {
            color: "#fff",
            fontSize: 14
          },
          text: "工程进度情况",
          x: "center"
        },
    radiusAxis: {
        type: 'category',
        data: ['v', 'w', 'x', 'y', 'z'],
        z: 10
    },
    polar: {
    },
    series: [{
        type: 'bar',
        data: [4, 3, 2, 1, 0],
        coordinateSystem: 'polar',
        name: 'Without Round Cap',
        //color: 'rgba(200, 0, 0, 0.5)',
        itemStyle: {
            borderColor: 'red',
            borderWidth: 1
        }
    }, {
        type: 'bar',
        data: [4, 3, 2, 1, 0],
        coordinateSystem: 'polar',
        name: 'With Round Cap',
        roundCap: true,
        //color: 'rgba(0, 200, 0, 0.5)',
        itemStyle: {
            borderColor: 'yellow',
            borderWidth: 1
        }
    }],
    legend: {
          orient: 'vertical',
          itemWidth: 15, //控制菱形多方
          icon: "diamond", //设置为菱形
          itemGap: 5, //图例之间的间隔
          top: 25, // 定位
          left: 10,
          center: "center",
          //icon: "roundRect", //icon为圆角矩形
          x: "center",
          y: "top",
          data:['Without Round Cap', 'With Round Cap'],
          textStyle: {
            //图例文字的样式
            color: "#fff",
            fontSize: 9,
          }
    }
      });
      // let _this = this;
      // window.addEventListener("resize",function(){
      //     _this.ChartLineGraph.resize();
      // })
    },
    initData1() {
      var myChart = echarts.init(document.getElementById("main2"));
      window.onresize = myChart.resize;
      // 绘制图表
      myChart.setOption({
        backround: "", //背景颜色透明
        title: {
          textStyle: {
            color: "#fff",
            fontSize: 14
          },
          text: "综合培训情况",
          x: "center"
        },
        tooltip: {
          trigger: "axis" //鼠标经过时提示
        },
        xAxis: {
          type: "category", //居中对齐
          axisLine: {
            lineStyle: {
              //color:'#104E8B',
              color: "#104E8B",
              width: 4
            }
            // 设置横纵轴颜色
          },
          axisLabel: {
            //show: true, // 是否显示刻度标签 默认显示
            fontSize: 7, // 文字的字体大小
            color: "#cdd3ee", // 刻度标签文字的颜色
            // 使用字符串模板，模板变量为刻度默认标签 {value}
            formatter: "{value}"
          },
          axisTick: {
            show: false // 是否显示坐标轴刻度 默认显示
          },
          data: [
            "货检",
            "调度",
            "调车",
            "本场",
            "客运",
            "行驶",
            "运转"
          ]
        },
        yAxis: {
          type: "value",
          splitLine: {
            show: true,
            lineStyle: {
              color: ["#104E8B"],
              width: 0.5,
              type: "dotted"
            }
          }, //设置网格线样式
          axisLine: {
            lineStyle: {
              color: "#104E8B",
              width: 4
            }
            // 设置横纵轴颜色
          },
          axisLabel: {
            show: true, // 是否显示刻度标签 默认显示
            fontSize: 6, // 文字的字体大小
            color: "#cdd3ee", // 刻度标签文字的颜色
            // 使用字符串模板，模板变量为刻度默认标签 {value}
            formatter: "{value}%"//设置百分数
          },
          axisTick: {
            show: false // 是否显示坐标轴刻度 默认显示
          }
        },

        series: [
          {
            itemStyle: { normal: { color: "#1a66ff" } }, //设置柱颜色
            data: [80, 75, 60, 82, 70, 50, 93],
            type: "bar",
            barMaxWidth: 25,
            itemStyle: {
              normal: {
                label: {
                  show: true, //开启显示
                  position: "top", //在上方显示
                  textStyle: {
                    //数值样式
                    color: "#fff",
                    fontSize: 6
                  }
                }
              }
            }
            // itemStyle : { normal: {label : {show: true}}} 显示在柱中
          }
        ]
      });
      // let _this = this;
      // window.addEventListener("resize",function(){
      //     _this.ChartLineGraph.resize();
      // })
    },
    initData2() {
      var myChart = echarts.init(document.getElementById("main3"));
      window.onresize = myChart.resize;
      // 绘制图表
      myChart.setOption({
        title: {
          textStyle: {
            color: "#fff",
            fontSize: 14
          },
          text: "中间站综合培训情况",
          x: "center"
        },
        xAxis: {
          type: "category",
          axisLine: {
            lineStyle: {
              //color:'#104E8B',
              color: "#104E8B",
              width: 4
            }
            // 设置横纵轴颜色
          },
          axisLabel: {
            fontSize: 7, // 文字的字体大小
            color: "#fff", // 刻度标签文字的颜色
            // 使用字符串模板，模板变量为刻度默认标签 {value}
            formatter: "{value}"
          },
          axisTick: {
            show: false // 是否显示坐标轴刻度 默认显示
          },
          data: [
            "小乔站",
            "柳林站",
            "孟庄站",
            "华南城站",
            "双湖大道站",
            "二七站",
            "花寨站"
          ]
        },
        yAxis: {
          splitLine: {
            show: true,
            lineStyle: {
              color: ["#104E8B"],
              width: 1,
              type: "dotted"
            }
          }, //设置
          type: "value",
          axisLine: {
            lineStyle: {
              //color:'#104E8B',
              color: "#104E8B",
              width: 4
            }
            // 设置横纵轴颜色
          },
          axisLabel: {
            show: true, // 是否显示刻度标签 默认显示
            fontSize: 6, // 文字的字体大小
            color: "#fff", // 刻度标签文字的颜色
            // 使用字符串模板，模板变量为刻度默认标签 {value}
            formatter: "{value}"
          },
          axisTick: {
            show: false // 是否显示坐标轴刻度 默认显示
          }
        },
        series: [
          {
            itemStyle: { normal: { color: "	#1a66ff" } }, //设置柱的颜色
            data: [75, 96, 92, 98, 50, 60, 85],
            type: "bar",
            barMaxWidth: 25,
            itemStyle: {
              normal: {
                label: {
                  show: true, //开启显示
                  position: "top", //在上方显示
                  textStyle: {
                    //数值样式
                    color: "#fff",
                    fontSize: 6
                  }
                }
              }
            }
          }
        ]
      });
      // let _this = this;
      // window.addEventListener("resize",function(){
      //     _this.ChartLineGraph.resize();
      // })
    }
  }
};
</script>
<style>
#bar1, #bar2,#bar3{
  float: left;
  border: 0.05rem solid #005580;
  margin: 0.35rem;
  box-shadow: 0 0 1px #99ccff;
  background-color: #064788;
  width: 100%;
  /* opacity: 0.9; */
}
</style>
 
 