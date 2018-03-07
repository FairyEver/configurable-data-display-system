<template>
  <div style="padding: 0px 10px 10px 10px;">
    <Button type="error" long @click="$emit('delete')">
      <Icon type="trash-a"></Icon>
      删除《{{activePageName}}》
    </Button>
  </div>
</template>

<script>
export default {
  props: {
    // 所有的页面
    pages: {
      type: Array,
      required: false,
      default: () => []
    },
    // 当前激活的页面
    active: {
      // 开始的时候是null 以后是数字
      required: false,
      default: null
    }
  },
  computed: {
    activePageName () {
      if (this.active === null) {
        return ''
      } else {
        return this.pages[this.active].title
      }
    }
  }
}
</script>
