<template>
  <!-- 这里的最外层是一定要东西的 -->
  <div id="app">
    <!-- 这里不能添加点击事件 需要从子组件中传递emit过来 -->
    <!-- @click 就是this.$on() 监听事件 @ v-on
    :即是js的区域 这样就可以动态传参  传变量
    :disabled="..." 引号里面是传递当前组件的参数， disabled是需要传递到子组件的参数，子组件需要props
  -->
    <el-button :loading="true" @click="doDefaultTap" size="large" :disabled="false" >默认按钮</el-button>
    <el-button @clickInner="doInnerIcon" icon="edit"  type="primary">主要按钮</el-button>
    <el-button type="text">文本按钮</el-button>
    <div>
      <el-button-group>
        <el-button type="primary" icon="arrow-left">上一页</el-button>
        <el-button type="primary">下一页<i class="el-icon-arrow-right  el-icon--right"></i></el-button>
      </el-button-group>
      <el-button-group>
        <el-button type="primary" icon="edit"></el-button>
        <el-button type="primary" icon="share"></el-button>
        <el-button type="primary" icon="delete"></el-button>
      </el-button-group>
    </div>
    <div>
      <el-button @click="dialogVisible=true" type="text" size="large">点击打开</el-button>
      <!-- 这里是传递 属性 visible 到子类  sync声明visible不在是props -->
      <el-dialog title="重要消息" :visible.sync="dialogVisible">
        <span>JerryLee is a good man！！！</span>
        <span slot="footer" class="dialog-footer">
          <el-button @click="dialogVisible=false">取消</el-button>
          <el-button @click="dialogVisible=false" type="success">确定</el-button>
        </span>
      </el-dialog>
    </div>
    <router-view></router-view>
  </div>
</template>

<script>
import ElDialog from '@/components/ElDialog.vue'
import ELButton from '@/components/ELButton.vue'
import ElButtonGroup from '@/components/ElButtonGroup.vue'

export default {
  data () {
    return {
      dialogVisible: false
    }
  },
  components: {
    "el-button": ELButton, //重新命名 ""字符串
    "el-button-group": ElButtonGroup,
    "el-dialog": ElDialog
  },
  methods: {
   doDefaultTap (evt) {
      alert('默认按钮！')
   },
   doInnerIcon (evt) {
     alert("点了小图标啦！")
   }
  }
}
</script>

<style>

</style>
