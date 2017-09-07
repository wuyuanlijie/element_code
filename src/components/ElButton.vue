XQ<template lang="html">
  <!-- 一定要有一个盒子 加了: 就是js区域 动态传参 -->
  <button class="el-button" @click="handleClick" :disabled="disabled"
     :class="[type?'el-button--'+type:'', size?'el-button--'+size:'',
       {  //分组化 {}无序的数组 []是有序的数组
         'is-disabled':disabled,
         'is-loading': loading,
         'is-plain': plain
       }
       ]" >
    <!-- 插槽 占位符 就可以在外面组件的中间插入值（传值）-->
    <i  class="el-icon-loading" v-if="loading"></i>
    <i  @click="handleInnerClick" :class="'el-icon-' + icon" v-if="icon&&!loading"></i>
    <!-- default默认的slot  -->
    <span v-if="$slots.default"><slot></slot></span>
  </button>
</template>

<script>
export default {
  props: {
    type: {
      type: String,
      default: 'default'
    },
    size: String,
    icon: {
      type: String,
      default: ''
    },
    // 父级向子级 传递参数
    disabled: Boolean,
    loading: Boolean,
    plain: Boolean,
    autofocus: Boolean
  },
  methods: {
    handleClick (evt) {
      // 调用事件对象
      this.$emit('click', evt)
    },
    handleInnerClick (evt) {
      this.$emit('clickInner', evt)
    }
  }
}
</script>

<style lang="css">
</style>
