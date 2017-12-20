<template>
  <el-button type="text" @click="open2">{{ message.text }}</el-button>
</template>


<script>
  // Vue.component('message-box', {
  //   props: ['message'],
  //   template: '<el-button type="text" @click="open2">{{ message.text }}</el-button>'
  // })

  export default {
    name: 'dialog',
    props: {
      messageOption: Object
    },
    data() {
      return {
        resolve: '',
        reject: '',
        promise: '' // 保存promise对象
      }
    },
    methods: {
      open2() {
        this.$confirm('是否需要清理缓存?', '提示', {
          confirmButtonText: '确定',
          cancelButtonText: '取消',
          type: 'warning'
        }).then(() => {
          this.$message({
            type: 'success',
            message: '清理成功!'
          });
        }).catch(() => {
          this.$message({
            type: 'info',
            message: '已取消'
          });          
        });
      }
    }
  }
</script>