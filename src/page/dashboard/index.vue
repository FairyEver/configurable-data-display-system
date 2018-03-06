<template>
  <cdds-maker v-bind="maker"></cdds-maker>
</template>

<script>
import data from './data.js'
const {
  stage: {
    cell: stageCell,
    height: stageHeight,
    width: stageWidth
  },
  pages
} = data
export default {
  components: {
    CddsMaker: () => import('@/components/cdds/maker/index.vue')
  },
  data () {
    return {
      maker: {
        stageCell: 0,
        stageHeight: 0,
        stageWidth: 0,
        pages: [],
        height: 'calc(100vh - 30px)'
      }
    }
  },
  mounted () {
    // 获取数据
    this.getData()
  },
  methods: {
    // 获取数据
    getData () {
      // 模拟数据请求赋值
      setTimeout(() => {
        this.maker.stageCell = stageCell
        this.maker.stageHeight = stageHeight
        this.maker.stageWidth = stageWidth
        this.maker.pages = pages
      }, 3000)
    }
  }
}
</script>
