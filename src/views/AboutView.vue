<template>
  <div class="about">
    <h1>This is an about page</h1>
    <el-row>
  <el-button>默认按钮</el-button>
  <el-button type="primary">主要按钮</el-button>
  <el-button type="success">成功按钮</el-button>
  <el-button type="info">信息按钮</el-button>
  <el-button type="warning">警告按钮</el-button>
  <el-button type="danger">危险按钮</el-button>
</el-row>
<el-carousel indicator-position="outside">
    <el-carousel-item v-for="item in 4" :key="item">
      <h3>{{ item }}</h3>
    </el-carousel-item>
  </el-carousel>
  <div class="echart" id="mychart" :style="myChartStyle"></div>
  <div>{{ time }}</div>
  </div>
</template>
<style>
  .el-carousel__item h3 {
    color: #475669;
    font-size: 18px;
    opacity: 0.75;
    line-height: 300px;
    margin: 0;
  }
  .el-carousel__item:nth-child(2n) {
    background-color: #99a9bf;
  }
  .el-carousel__item:nth-child(2n+1) {
    background-color: #d3dce6;
  }
</style>
<script>
import * as echarts from 'echarts'
export default {
  data () {
    return {
      xData: ['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun'],
      yData: [23, 24, 18, 25, 27, 28, 25],
      myChartStyle: { float: 'left', width: '100%', height: '400px' },
      time: this.$moment().format('YYYY-MM-DD hh:mm:ss')
    }
  },
  mounted () {
    this.initEcharts()
  },
  methods: {
    initEcharts () {
      const option = {
        xAxis: {
          data: this.xData
        },
        yAxis: {},
        series: [
          {
            type: 'bar',
            data: this.yData
          }
        ]
      }
      const myChart = echarts.init(document.getElementById('mychart'))
      myChart.setOption(option)
      window.addEventListener('resize', () => {
        myChart.resize()
      })
    }
  }
}
</script>
