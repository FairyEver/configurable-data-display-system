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
      type: Number,
      required: false,
      default: null
    }
  },
  computed: {
    // 返回现在激活页面的名称
    activePageName () {
      return this.pages[this.active].title
    }
  }
}
</script>
