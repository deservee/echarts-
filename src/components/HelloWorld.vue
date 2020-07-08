<template>
  <div id="all">
    <div class="contains">
      <!-- <img src="../assets/head.PNG"> -->
      <div id="top">vue-echarts可视</div>

      <div id="content">
        <div class="left">
          <div id="myChart1" :style="{width: '100%', height: '180px'}"></div>
          <div id="myChart4" :style="{width: '100%', height: '180px'}"></div>
          <div id="myChart7" :style="{width: '100%', height: '180px'}"></div>
        </div>
        <div class="center">
          <myEcharts></myEcharts>
        </div>
        <div class="right">
          <div id="myChart3" :style="{width: '100%', height: '180px'}"></div>
          <div id="myChart6" :style="{width: '100%', height: '180px'}"></div>
          <div id="myChart9" :style="{width: '100%', height: '180px'}"></div>
        </div>
      </div>
      <!-- <div id="bottom">bottom</div> -->
    </div>
  </div>
</template>


<script>
//import total from "../demo/total.vue";
import myEcharts from "../demo/myEcharts.vue";
// 引入基本模板
let echarts = require("echarts/lib/echarts");
// 引入柱状图组件
require("echarts/lib/chart/bar");
require("echarts/lib/chart/line");
require("echarts/lib/chart/pie");

// 引入提示框和title组件
require("echarts/lib/component/tooltip");
require("echarts/lib/component/title");
export default {
  components: {
    // total
    myEcharts
  },
  data() {
    return {};
  },
  methods: {
    drawLine1() {
      // 基于准备好的dom，初始化echarts实例
      let myChart1 = this.$echarts.init(document.getElementById("myChart1"));
      // 绘制图表
      myChart1.setOption({
        tooltip: {
        trigger: 'item',
        formatter: '{a} <br/>{b}: {c} ({d}%)'
    },
     title: {
          textStyle: {
            color: "#fff",
            fontSize: 14
          },
          text: "广告宣传情况",
          x: "center"
        },
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
          data:['直达', '营销广告', '搜索引擎', '邮件营销', '联盟广告', '视频广告', '百度'],
          textStyle: {
            //图例文字的样式
            color: "#fff",
            fontSize: 9
          }
    },
    series: [
        {
            name: '访问来源',
            type: 'pie',
            selectedMode: 'single',
            radius: [0, '30%'],

            label: {
                position: 'inner'
            },
            labelLine: {
                show: false
            },
            data: [
                {value: 335, name: '直达', selected: true},
                {value: 679, name: '营销广告'},
                {value: 1548, }
            ]
        },
        {
            name: '访问来源',
            type: 'pie',
            radius: ['40%', '55%'],
            label: {
              
                rich: {
                    a: {
                        color: '#999',
                        lineHeight: 22,
                        align: 'center'
                    },
                    
                    hr: {
                        borderColor: '#aaa',
                        width: '100%',
                        borderWidth: 0.5,
                        height: 0
                    },
                    b: {
                        fontSize: 16,
                        lineHeight: 33
                    },
                    per: {
                        color: '#eee',
                        backgroundColor: '#334455',
                        padding: [2, 4],
                        borderRadius: 2
                    }
                }
            },
            data: [
                {value: 335, name: '直达'},
                {value: 310, name: '邮件营销'},
                {value: 234, name: '联盟广告'},
                {value: 135, name: '视频广告'},
                {value: 1048, name: ''},
            ]
        }
    ]
      });
    },
    drawLine3() {
      // 基于准备好的dom，初始化echarts实例 get
      let myChart3 = this.$echarts.init(document.getElementById("myChart3"));
      // 绘制图表
       myChart3.setOption({
        title: {
          textStyle: {
            color: "#fff",
            fontSize: 14
          },
          text: "日常培训",
          x: "center"
        },
        backgroundColor: "", //背景颜色透明
        tooltip: {
          trigger: "axis" //鼠标经过提示
        },
        legend: {
          itemWidth: 15, //控制菱形多方
          icon: "diamond", //设置为菱形
          itemGap: 5, //图例之间的间隔
          top: 25, // 定位
          left: 20,
          center: "center",
          //icon: "roundRect", //icon为圆角矩形
          x: "center",
          y: "top",
          data: ["班前一考", "班前提问", "应急演练", "星级考试", "月度抽考"],
          textStyle: {
            //图例文字的样式
            color: "#fff",
            fontSize: 9
          }
        },
        grid: {
          left: 0,
          top: "25%",
          right: 0,
          bottom: "10%",
          containLabel: true
        },
        xAxis: {
          //data: arrDate,
          type: "category",
          axisLine: {
            lineStyle: {
              //color:'#104E8B',
              color: "#cdd3ee"
            }
            // 设置横纵轴颜色
          },
          axisLabel: {
            fontSize: 6, // 文字的字体大小
            color: "#fff", // 刻度标签文字的颜色
            // 使用字符串模板，模板变量为刻度默认标签 {value}
            formatter: "{value}"
          },
          axisTick: {
            show: false // 是否显示坐标轴刻度 默认显示
          },
          data: [
            "01",
            "02",
            "03",
            "04",
            "05",
            "06",
            "07",
            "08",
            "09",
            "10",
            "11",
            "12",
            "13",
            "14",
            "15",
            "16",
            "17",
            "18",
            "19",
            "20",
            "21",
            "22",
            "23",
            "24",
            "25",
            "26",
            "27",
            "28",
            "29",
            "30"
          ]
        },
        yAxis: {
          type: "value",
          //splitLine: { show: false }, //去除网格线
          //show: false, //隐藏y轴
           interval: 15, //设置纵轴间隔
           min:0,
           max:60,
          splitLine: {
            show: true,
            lineStyle: {
              color: ["#104E8B"],
              width: 1,
              type: "dotted"
            }
          }, //设置网格线样式
          axisLine: {
            show: false
            // 设置纵轴隐藏
          },
          axisLabel: {
            show: true, // 是否显示刻度标签 默认显示
            fontSize: 6, // 文字的字体大小
            color: "#cdd3ee", // 刻度标签文字的颜色
            // 使用字符串模板，模板变量为刻度默认标签 {value}
            formatter: "{value}"
          },
          axisTick: {
            show: false // 是否显示坐标轴刻度 默认显示
          }
        },
        color: ["#1DB0B8", "#37C6C0", "#D0E9FF", "#c7353a", "#f5b91e"],
        series: [
          {
            name: "班前一考",
            areaStyle: {},//向下渲染颜色
            type: "line",
            symbol:"none",
            itemStyle: {
              normal: {
                color: "orange",
                lineStyle: {
                  // 系列级个性化折线样式
                  width: 2,
                  type: "solid",
                  // color: new echarts.graphic.LinearGradient(0, 0, 0, 1, [
                  //   {
                  //     offset: 0,
                  //     color: "green"
                  //   },
                  //   {
                  //     offset: 1,
                  //     color: "red"
                  //   }
                  // ]) //线条渐变色
                }
              },
              emphasis: {
                color: "red",
                lineStyle: {
                  // 系列级个性化折线样式
                  width: 2,
                  type: "dotted",
                  color: new echarts.graphic.LinearGradient(0, 0, 0, 1, [
                    {
                      offset: 0,
                      color: "green"
                    },
                    {
                      offset: 1,
                      color: "red"
                    }
                  ])
                }
              }
            }, //线条样式
            data: [15, 14, 15, 13, 15, 12, 14, 16,15, 14, 15, 13, 15, 12, 14, 16]
          },
          {
            name: "班前提问",
            type: "line",
            areaStyle: {},
            symbol:"none",
            itemStyle: {
              normal: {
                color: "pink",
                lineStyle: {
                  // 系列级个性化折线样式
                  width: 2,
                  type: "solid",
                  // color: new echarts.graphic.LinearGradient(0, 0, 0, 1, [
                  //   {
                  //     offset: 0,
                  //     color: "green"
                  //   },
                  //   {
                  //     offset: 1,
                  //     color: "red"
                  //   }
                  // ]) //线条渐变色
                  
                }
              },
              emphasis: {
                color: "red",
                lineStyle: {
                  // 系列级个性化折线样式
                  width: 2,
                  type: "dotted",
                  color: new echarts.graphic.LinearGradient(0, 0, 0, 1, [
                    {
                      offset: 0,
                      color: "green"
                    },
                    {
                      offset: 1,
                      color: "red"
                    }
                  ])
                }
              }
            }, //线条样式
            data: [20, 23, 21, 24, 25, 21, 25, 22, 20, 23, 21, 24, 25, 21, 25, 22]
          },
          {
            name: "应急演练",
            areaStyle: {},
            type: "line",
            symbol:"none",
            itemStyle: {
              normal: {
                color: "#008B45",
                lineStyle: {
                  // 系列级个性化折线样式
                  width: 2,
                  type: "solid",
                  color: new echarts.graphic.LinearGradient(0, 0, 0, 1, [
                    {
                      offset: 0,
                      color: "#8470FF"
                    },
                    {
                      offset: 1,
                      color: "#008B45"
                    }
                  ]) //线条渐变色
                }
              },
              emphasis: {
                color: "#008B45",
                lineStyle: {
                  // 系列级个性化折线样式
                  width: 2,
                  type: "dotted",
                  color: new echarts.graphic.LinearGradient(0, 0, 0, 1, [
                    {
                      offset: 0,
                      color: "#00FFFF"
                    },
                    {
                      offset: 1,
                      color: "#5F9EA0"
                    }
                  ])
                }
              }
            }, //线条样式
            data: [28, 32, 28, 30, 29, 30, 27, 30, 28, 32, 28, 30, 29, 30, 27, 30]
          },
          {
            name: "星级考试",
            areaStyle: {},
            type: "line",
            symbol:"none",
            itemStyle: {
              normal: {
                color: "red",
                lineStyle: {
                  // 系列级个性化折线样式
                  width: 2,
                  type: "solid",
                  // color: new echarts.graphic.LinearGradient(0, 0, 0, 1, [
                  //   {
                  //     offset: 0,
                  //     color: "green"
                  //   },
                  //   {
                  //     offset: 1,
                  //     color: "red"
                  //   }
                  // ]) //线条渐变色
                }
              },
              emphasis: {
                color: "red",
                lineStyle: {
                  // 系列级个性化折线样式
                  width: 2,
                  type: "dotted",
                  color: new echarts.graphic.LinearGradient(0, 0, 0, 1, [
                    {
                      offset: 0,
                      color: "green"
                    },
                    {
                      offset: 1,
                      color: "red"
                    }
                  ])
                }
              }
            }, //线条样式
            data: [32, 35, 32, 38, 35, 33, 33, 33, 32, 35, 32, 38, 35, 33, 33, 33]
          },
          {
            name: "月度抽考",
            areaStyle: {},
            type: "line",
            symbol:"none",
            itemStyle: {
              color: "#6A5ACD",
              normal: {
                lineStyle: {
                  // 系列级个性化折线样式
                  width: 2,
                  type: "solid",
                  color: new echarts.graphic.LinearGradient(0, 0, 0, 1, [
                    {
                      offset: 0,
                      color: "#0000FF"
                    },
                    {
                      offset: 1,
                      color: "#CD5C5C"
                    }
                  ]) //线条渐变色
                }
              },
              emphasis: {
                color: "#6A5ACD",
                lineStyle: {
                  // 系列级个性化折线样式
                  width: 2,
                  type: "dotted",
                  color: new echarts.graphic.LinearGradient(0, 0, 0, 1, [
                    {
                      offset: 0,
                      color: "#1E90FF"
                    },
                    {
                      offset: 1,
                      color: "#0000FF"
                    }
                  ])
                }
              }
            }, //线条样式
            areaStyle: {
              normal: {
                //颜色渐变函数 前四个参数分别表示四个位置依次为左、下、右、上
                color: new echarts.graphic.LinearGradient(0, 0, 0, 1, [
                  {
                    offset: 0,
                    color: "rgba(80,141,255,0.39)"
                  },
                  {
                    offset: 0.34,
                    color: "rgba(56,155,255,0.25)"
                  },
                  {
                    offset: 1,
                    color: "rgba(38,197,254,0.00)"
                  }
                ])
              }
            }, //区域颜色渐变
            data: [50, 43, 41, 44, 50, 43, 51, 42, 50, 43, 41, 44, 50, 43, 51, 42]
          }
        ]
      });
    },
    drawLine4() {
      // 基于准备好的dom，初始化echarts实例
      let myChart4 = this.$echarts.init(document.getElementById("myChart4"));
      // 绘制图表
      myChart4.setOption({
        title: {
          textStyle: {
            color: "#fff",
            fontSize: 14
          },
          text: "季度轮训",
          x: "center"
        },
        legend: {
          textStyle: {
            // 文本样式
            fontSize: 9,
            color: "#cdd3ee"
          },
          itemWidth: 15, //控制菱形多方
          icon: "diamond", //设置为菱形
          itemGap: 5, //图例之间的间隔
          top: 25, // 定位
          left: 20,
          center: "center",
          data: ["行车", "调车", "配车", "货检", "客运"] // 图例的数据数组
          //x:'left'
        },
        grid: {
          x: 30, // 左间距
          y: 55, // 上间距
          x2: 20, // 右间距
          y2: 20 // 下间距
        },
        tooltip: {},
        dataset: {
          // 提供一份数据。
          source: [
            ["product", "行车", "调车", "配车", "货检", "客运"],
            ["四月", 115, 98, 80, 65, 90],
            ["五月", 110, 110, 60, 92, 78],
            ["六月", 48, 36, 48, 25, 19]
          ]
        },
        // 声明一个 X 轴，类目轴（category）。默认情况下，类目轴对应到 dataset 第一列。
        xAxis: {
          type: "category", //居中对齐
          axisLine: {
            lineStyle: {
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
          }
        },
        // 声明一个 Y 轴，数值轴。
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
            formatter: "{value}" //设置百分数
          },
          axisTick: {
            show: false // 是否显示坐标轴刻度 默认显示
          },
          interval: 25, //设置纵轴间隔
          min: 0,
          max: 125
        },
        // 声明多个 bar 系列，默认情况下，每个系列会自动对应到 dataset 的每一列。
        series: [
          {
            //itemStyle: { normal: { color: "#1a66ff" } }, //设置柱颜色
            type: "bar",
            barMaxWidth: 10,
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
          },
          {
            type: "bar",
            barMaxWidth: 10,
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
          },
          {
            type: "bar",
            barMaxWidth: 10,
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
          },
          {
            type: "bar",
            barMaxWidth: 10,
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
          },
          {
            type: "bar",
            barMaxWidth: 10,
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
    },

    drawLine6() {
      // 基于准备好的dom，初始化echarts实例
      let myChart6 = this.$echarts.init(document.getElementById("myChart6"));
      // 绘制图表
      myChart6.setOption({
        // backgroundColor:'#fff',设置背景颜色
        title: {
          textStyle: {
            // 文本样式
            fontSize: 14,
            color: "#cdd3ee"
          },
          text: "重点培训",
          x: "center"
        },
        grid: {
          x: 40, // 左间距
          y: 70, // 上间距
          x2: 20, // 右间距
          y2: 40 // 下间距
        },
        legend: {
          //orient: 'vertical',//垂直布局
          textStyle: {
            // 文本样式
            fontSize: 9,
            color: "#cdd3ee"
          },
          itemWidth: 15, //控制菱形多方
          icon: "diamond", //设置为菱形
          itemGap: 25, //图例之间的间隔
          top: 30, // 定位
          center: "center",
          data: ["实培人数", "应培人数"] // 图例的数据数组
          //x:'left'
        },
        xAxis: {
          type: "category", //居中对齐
          axisLine: {
            lineStyle: {
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
            interval: 0,
            rotate: 40, //坐标斜放
            formatter: "{value}"
          },
          axisTick: {
            show: false // 是否显示坐标轴刻度 默认显示
          },
          boundaryGap: false, //设置从0纵坐标开始
          data: [
            "调图培训",
            "电气化培训",
            "防洪培训",
            "劳安培训",
            "防暑降温培训",
            "防寒过冬培训",
            "施工培训",
            "其他"
          ]
        },
        yAxis: {
          interval: 400, //设置纵轴间隔
          splitLine: {
            show: true,
            lineStyle: {
              color: ["#104E8B"],
              width: 1,
              type: "dotted"
            }
          }, //设置网格线样式
          axisLine: {
            show: false
            // 设置纵轴隐藏
          },
          axisLabel: {
            show: true, // 是否显示刻度标签 默认显示
            fontSize: 6, // 文字的字体大小
            color: "#cdd3ee", // 刻度标签文字的颜色
            // 使用字符串模板，模板变量为刻度默认标签 {value}
            formatter: "{value}"
          },
          axisTick: {
            show: false // 是否显示坐标轴刻度 默认显示
          }
        },
        series: [
          {
            name: "实培人数",
            data: [693, 934, 902, 921, 1112, 0, 705, 0],
            type: "line",
            color: "#ff4d4d",
            itemStyle: {
              normal: {
                label: { show: true, color: "white", fontSize: 6 }
              }
            } //设置折线上数值,并设置颜色
            //smoooth:0.2,
            //orient: 'vertical',//垂直布局
          },
          {
            name: "应培人数",
            data: [705, 934, 910, 1134, 1134, 1159, 705, 0],
            type: "line",
            color: "#ffc266",
            itemStyle: {
              normal: { label: { show: true, color: "white", fontSize: 6 } }
            }
            //smoooth:0.2,
          }
        ]
      });
    },
    drawLine7() {
      // 基于准备好的dom，初始化echarts实例
      let myChart7 = this.$echarts.init(document.getElementById("myChart7"));
      // 绘制图表
      myChart7.setOption({
         title: {
          textStyle: {
            // 文本样式
            fontSize: 14,
            color: "#cdd3ee"
          },
          text: "一周总结",
          x: "center"
        },
          tooltip: {
        trigger: 'axis',
        axisPointer: {            // 坐标轴指示器，坐标轴触发有效
            type: 'shadow'        // 默认为直线，可选为：'line' | 'shadow'
        }
    },
    legend: {
        textStyle: {
            // 文本样式
            fontSize: 9,
            color: "#cdd3ee"
          },
          itemWidth: 15, //控制菱形多方
          icon: "diamond", //设置为菱形
          itemGap: 5, //图例之间的间隔
          top: 25, // 定位
          left: 20,
          center: "center",
        data: ['直接访问', '邮件营销', '联盟广告', '视频广告', '搜索引擎']
    },
    grid: {
        left: '3%',
        right: '4%',
        bottom: '3%',
        containLabel: true
    },
    xAxis: {
       splitLine: {
            show: true,
            lineStyle: {
              color: ["#104E8B"],
              width: 1,
              type: "dotted"
            }
          },
      type: 'value',
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
          data: []
    },
    yAxis: {
             // 坐标轴类型,  'category' 类目轴，适用于离散的类目数据
             // 为该类型时必须通过 data 设置类目数据
             type: "category",
             // 坐标轴刻度
             axisTick: {
               show: false // 是否显示坐标轴刻度 默认显示
             },
             // 坐标轴轴线
             axisLine: {
               // 是否显示坐标轴轴线 默认显示
               show: false, // 是否显示坐标轴轴线 默认显示
               lineStyle: {
                 // 坐标轴线线的颜色
                 color: "#cdd3ee"
               }
             },
             // 坐标轴在图表区域中的分隔线
             splitLine: {
               show: false // 是否显示分隔线。默认数值轴显示
             },
             // 坐标轴刻度标签
             axisLabel: {
               show: true, // 是否显示刻度标签 默认显示
               fontSize: 7, // 文字的字体大小
               color: "#cdd3ee", // 刻度标签文字的颜色
               // 使用字符串模板，模板变量为刻度默认标签 {value}
               formatter: "{value}"
             },
             type: 'category',
             fontSize:9,
              data: ['周一', '周二', '周三', '周四', '周五', '周六', '周日']
         
    },
    series: [
        {
            name: '直接访问',
            type: 'bar',
            stack: '总量',
            label: {
                show: true,
                position: 'insideRight',
                fontSize:7,
            },
            data: [320, 302, 301, 334, 390, 330, 320]
        },
        {
            name: '邮件营销',
            type: 'bar',
            stack: '总量',
            label: {
                show: true,
                position: 'insideRight',
                fontSize:7,
            },
            data: [120, 132, 101, 134, 90, 230, 210]
        },
        {
            name: '联盟广告',
            type: 'bar',
            stack: '总量',
            label: {
                show: true,
                position: 'insideRight',
                fontSize:7,
            },
            data: [220, 182, 191, 234, 290, 330, 310]
        },
        {
            name: '视频广告',
            type: 'bar',
            stack: '总量',
            label: {
                show: true,
                position: 'insideRight',
                fontSize:7,
            },
            data: [150, 212, 201, 154, 190, 330, 410]
        },
        {
            name: '搜索引擎',
            type: 'bar',
            stack: '总量',
            label: {
                show: true,
                position: 'insideRight',
                fontSize:7,
            },
            data: [820, 832, 901, 934, 1290, 1330, 1320]
        }
    ]
        // title: {
        //   textStyle: {
        //     color: "#fff",
        //     fontSize: 14
        //   },
        //   text: "师资评价",
        //   x: "center"
        // },
        // color: ["#3366FF", "#FF3333", "#FFF"],
        // // 设置图表的位置
        // grid: {
        //   x: 60, // 左间距
        //   y: 55, // 上间距
        //   x2: 20, // 右间距
        //   y2: 20 // 下间距
        // },
        // // 提示框组件
        // tooltip: {
        //   trigger: "axis", // 触发类型, axis: 坐标轴触发
        //   axisPointer: {
        //     // 指示器类型  'line' 直线指示器 'shadow' 阴影指示器 'none' 无指示器
        //     // 'cross' 十字准星指示器 其实是种简写，表示启用两个正交的轴的 axisPointer
        //     type: ""
        //   },
        //   textStyle: {
        //     color: "#cdd3ee", // 文字颜色
        //     fontFamily: "Microsoft YaHei"
        //   },
        //   // 提示框浮层内容格式器，支持字符串模板和回调函数两种形式 折线（区域）图、柱状（条形）图、K线图
        //   // {a}（系列名称），{b}（类目值），{c}（数值）, {d}（无）
        //   formatter: "{b}<br />{a0}: {c0}%<br />{a1}: {c1}%<br />{a2}: {c2}%"
        // },
        // // 图例组件
        // legend: {
        //   textStyle: {
        //     // 文本样式
        //     fontSize: 9,
        //     color: "#cdd3ee"
        //   },
        //   itemWidth: 15, //控制菱形多方
        //   icon: "diamond", //设置为菱形
        //   itemGap: 20, //图例之间的间隔
        //   top: 35, // 定位
        //   left: 20,
        //   data: ["学时", "满意度"] // 图例的数据数组
        //   //x:'left'
        // },
        // // X轴
        // xAxis: {
        //   type: "value", // 坐标轴类型,   'value' 数值轴，适用于连续数据
        //   // 坐标轴刻度
        //   axisTick: {
        //     show: false // 是否显示坐标轴刻度 默认显示
        //   },
        //   // 坐标轴轴线
        //   axisLine: {
        //     // 是否显示坐标轴轴线 默认显示
        //     show: false // 是否显示坐标轴轴线 默认显示
        //   },
        //   // 坐标轴在图表区域中的分隔线
        //   splitLine: {
        //     show: false // 是否显示分隔线。默认数值轴显示
        //   },
        //   // 坐标轴刻度标签
        //   axisLabel: {
        //     show: false // 是否显示刻度标签 默认显示
        //   }
        // },
        // yAxis: [
        //   // 左侧Y轴
        //   {
        //     // 坐标轴类型,  'category' 类目轴，适用于离散的类目数据
        //     // 为该类型时必须通过 data 设置类目数据
        //     type: "category",
        //     // 坐标轴刻度
        //     axisTick: {
        //       show: false // 是否显示坐标轴刻度 默认显示
        //     },
        //     // 坐标轴轴线
        //     axisLine: {
        //       // 是否显示坐标轴轴线 默认显示
        //       show: false, // 是否显示坐标轴轴线 默认显示
        //       lineStyle: {
        //         // 坐标轴线线的颜色
        //         color: "#cdd3ee"
        //       }
        //     },
        //     // 坐标轴在图表区域中的分隔线
        //     splitLine: {
        //       show: false // 是否显示分隔线。默认数值轴显示
        //     },
        //     // 坐标轴刻度标签
        //     axisLabel: {
        //       show: true, // 是否显示刻度标签 默认显示
        //       fontSize: 12, // 文字的字体大小
        //       color: "#cdd3ee", // 刻度标签文字的颜色
        //       // 使用字符串模板，模板变量为刻度默认标签 {value}
        //       formatter: "{value}"
        //     },
        //     // 类目数据，在类目轴（type: 'category'）中有效

        //     data: [名字]
        //   }
        // ],
        // // 系列列表
        // series: [
        //   {
        //     type: "bar", // 系列类型
        //     name: "学时", // 系列名称, 用于tooltip的显示, legend 的图例筛选
        //     // 数据堆叠，同个类目轴上系列配置相同的stack值后，后一个系列的值会在前一个系列的值上相加
        //     stack: "总量",
        //     barMaxWidth: 16, // 柱条的最大宽度，不设时自适应
        //     // 图形上的文本标签
        //     label: {
        //       show: true, //控制表格上是否显示数字
        //       // 标签的位置 left right bottom top inside  // 绝对的像素值 position: [10, 10]
        //       // 相对的百分比
        //       //position: ['50%', '50%']
        //       position: "inside"
        //     },
        //     data: [0, 48, 26, 11, 20, 12] // 系列中的数据内容数组
        //   },
        //   {
        //     type: "bar", // 系列类型
        //     name: "满意度", // 系列名称, 用于tooltip的显示, legend 的图例筛选
        //     // 数据堆叠，同个类目轴上系列配置相同的stack值后，后一个系列的值会在前一个系列的值上相加
        //     stack: "总量",
        //     barMaxWidth: 16, // 柱条的最大宽度，不设时自适应
        //     // 图形上的文本标签
        //     label: {
        //       show: true,
        //       // 标签的位置 left right bottom top inside  // 绝对的像素值 position: [10, 10]
        //       // 相对的百分比 position: ['50%', '50%']
        //       position: "inside"
        //     },
        //     data: [0, 8, 38, 60, 30, 40] // 系列中的数据内容数组
        //   },
        //   {
        //     type: "bar", // 系列类型
        //     name: "", // 系列名称, 用于tooltip的显示, legend 的图例筛选
        //     // 数据堆叠，同个类目轴上系列配置相同的stack值后，后一个系列的值会在前一个系列的值上相加
        //     stack: "总量",
        //     barMaxWidth: 16, // 柱条的最大宽度，不设时自适应
        //     // 图形上的文本标签
        //     label: {
        //       show: true,
        //       // 标签的位置 left right bottom top inside  // 绝对的像素值 position: [10, 10]
        //       // 相对的百分比 position: ['50%', '50%']
        //       position: "inside"
        //     },
        //     data: [0, 44, 36, 29, 50, 48] // 系列中的数据内容数组
        //   }
        // ]
      });
    },
    drawLine9() {
      // 基于准备好的dom，初始化echarts实例
      let myChart9 = this.$echarts.init(document.getElementById("myChart9"));
      // 绘制图表
      myChart9.setOption({
        title: {
         textStyle: {
            // 文本样式
            fontSize: 14,
            color: "#cdd3ee"
          },
          text: "基础雷达图",
          x: "center"
    },
    tooltip: {},
    legend: {
       textStyle: {
            // 文本样式
            fontSize: 9,
            color: "#cdd3ee"
          },
          itemWidth: 15, //控制菱形多方
          icon: "diamond", //设置为菱形
          itemGap: 25, //图例之间的间隔
          top: 20, // 定位
          center: "center",
          data: ["预算分配", "实际开销"] 
    },
    radar: {
        // shape: 'circle',
        name: {
            textStyle: {
                color: '#fff',
                //backgroundColor: '#999',
                borderRadius: 3,
                //padding: [2, 2]
                
            }
        },
        indicator: [
            { name: '销售', max: 6500},
            { name: '管理', max: 16000},
            { name: '信息技术', max: 30000},
            { name: '客服', max: 38000},
            { name: '研发', max: 52000},
            { name: '市场', max: 25000}
        ]
    },
    series: [{
        name: '预算 vs 开销',
        type: 'radar',
        // areaStyle: {normal: {}},
        data: [
            {
                value: [4300, 10000, 28000, 35000, 50000, 19000],
                name: '预算分配'
            },
            {
                value: [5000, 14000, 28000, 31000, 42000, 21000],
                name: '实际开销'
            }
        ]
    }]
      });
    }
  },

  created() {},
  mounted() {
    this.drawLine1();
    this.drawLine3();
    this.drawLine4();
    this.drawLine6();
    this.drawLine7();
    this.drawLine9();
    //实现自适应部分
    window.addEventListener("resize", () => {
      this.$echarts.init(document.getElementById("myChart1")).resize();
    });
    //实现自适应部分
    window.addEventListener("resize", () => {
      this.$echarts.init(document.getElementById("myChart3")).resize();
    });
    window.addEventListener("resize", () => {
      this.$echarts.init(document.getElementById("myChart4")).resize();
    });
    window.addEventListener("resize", () => {
      this.$echarts.init(document.getElementById("myChart6")).resize();
    });
    window.addEventListener("resize", () => {
      this.$echarts.init(document.getElementById("myChart7")).resize();
    });
    window.addEventListener("resize", () => {
      this.$echarts.init(document.getElementById("myChart9")).resize();
    });
  }
};
</script>
<style>
#chart {
  display: flex;
}
#all {
  margin: 0;
  padding: 0;
  width: 100%;
  height: 100%;
}
.contains {
  width: 100%;
  min-width: 500px;
}
#top {
  position: absolute;
  top: 0;
  left: 0;
  background-color: rgb(95, 104, 180);
  height: 60px;
  line-height: 60px;
  font-size: 1.5rem;
  width: 100%;
  z-index: 100;
  /* opacity: 0.8; */
  font-family: "Courier New", Courier, monospace;
}
#content {
  position: absolute;
  width: 100%;
  /* min-width: 600px; */
  /* overflow:auto; */
  /* background-color: #f0e6a2; */
  /* bottom: 100px; */
  top: 60px;
  left: 0;
  right: 0;
  z-index: 90;
  display: flex;
  flex-direction: row;
}
.left {
  width: 30%;
  height: 100%;
  float: left;
  margin: 0.4rem;
  /* min-width: 300px; */
}
 #myChart1,#myChart3,#myChart4,#myChart6,#myChart7,#myChart9 {
  float: left;
  border: 0.05rem solid #005580;
  margin: 0.35rem;
  box-shadow: 0 0 1px #99ccff;
  background-color: #064788;
}
.center {
  width: 40%;
  height: 100%;
  /* background-color: skyblue;   */
  float: left;
  margin: 0.4rem;
}

.right {
  width: 30%;
  height: 100%;
  float: left;
  /* min-width: 300px; */
  margin: 0.4rem;
}
</style>
