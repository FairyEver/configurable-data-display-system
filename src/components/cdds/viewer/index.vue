<template>
  <div :style="stageStyle" class="stage">
    <!-- 网格布局 -->
    <template v-if="page.type === 'grid'">
      grid
    </template>
    <!-- 自由布局 -->
    <template v-if="page.type === 'free'">
      free
    </template>
    <!-- <grid-layout
      :layout="layout"
      :col-num="12"
      :row-height="30"
      :is-draggable="true"
      :is-resizable="true"
      :is-mirrored="false"
      :vertical-compact="true"
      :margin="[10, 10]"
      :use-css-transforms="true">
      <grid-item
        v-for="(item, index) in layout"
        :key="index"
        :x="item.x"
        :y="item.y"
        :w="item.w"
        :h="item.h"
        :i="item.i">
        {{item.i}}
      </grid-item>
    </grid-layout> -->
  </div>
</template>

<script>
import {GridLayout, GridItem} from 'vue-grid-layout'
export default {
  name: 'cdds-viewer',
  components: {
    GridLayout,
    GridItem
  },
  props: {
    // 舞台 单位尺寸
    cell: {
      type: Number,
      required: false,
      default: 1
    },
    // 舞台 宽度
    width: {
      type: Number,
      required: false,
      default: 192
    },
    // 舞台 高度
    height: {
      type: Number,
      required: false,
      default: 108
    },
    // 页面数据
    page: {
      type: Object,
      required: false,
      default: () => ({})
    }
  },
  data () {
    return {
      layout: [
        {"x":0,"y":0,"w":2,"h":2,"i":"0"},
        {"x":2,"y":0,"w":2,"h":4,"i":"1"},
        {"x":4,"y":0,"w":2,"h":5,"i":"2"},
        {"x":6,"y":0,"w":2,"h":3,"i":"3"},
        {"x":8,"y":0,"w":2,"h":3,"i":"4"}
      ]
    }
  },
  computed: {
    stageStyle () {
      return {
        width: this.cell * this.width + 'px',
        height: this.cell * this.height + 'px'
      }
    }
  }
}
</script>

<style scoped>
.stage {
  background-color: #FFF;
}
</style>
