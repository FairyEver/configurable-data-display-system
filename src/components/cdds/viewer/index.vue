<template>
  <div :style="stageStyle" class="stage">
    <!-- 网格布局 -->
    <template v-if="page.type === 'grid'">
      <grid-layout
      :layout="gridLayout"
      :col-num="gridColNum"
      :row-height="gridRowHeight">
      <grid-item
        v-for="(item, index) in gridLayout"
        :key="index"
        :x="item.x"
        :y="item.y"
        :w="item.w"
        :h="item.h"
        :i="item.i">
        [{{item.i}}]
      </grid-item>
    </grid-layout>
    </template>
    <!-- 自由布局 -->
    <template v-if="page.type === 'free'">
      free
      {{page}}
    </template>
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
      // :is-draggable="true"
      // :is-resizable="true"
      // :is-mirrored="false"
      // :vertical-compact="true"
      // :margin="[10, 10]"
      // :use-css-transforms="true"
      // type = grid 时生效
      gridColNum: 0,
      gridRowHeight: 0,
      gridLayout: []
    }
  },
  computed: {
    // 舞台样式 主要是设置尺寸
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
