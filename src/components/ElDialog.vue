<template lang="html">
  <transition name="dialog-fade">
    <div class="el-dialog__wrapper" v-show="visible">
      <div class="el-dialog">
        <div class="el-dialog__header">
          <span class="el-dialog__title">
            {{title}}
          </span>
          <button type="button" aria-label="Close" class="el-dialog__headerbtn">
            <i class="el-dialog__close el-icon-close"></i>
          </button>
        </div>
        <div class="el-dialog__body">
          <slot></slot>
        </div>
        <div class="el-dialog__footer" v-if="$slots.footer">
          <slot name="footer"></slot>
        </div>
      </div>
    </div>
  </transition>
</template>

<script>
export default {
  name: 'ElDialog',
  watch: {
    // 监听数据的改变
    visible(val) {
      this.$emit('update:visible', val)
    }
  },
  props: {
    visible: Boolean,
    title: {
      type: String,
      default: ''
    }
  }
}
</script>

<style lang="css">
</style>
