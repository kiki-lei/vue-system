<template>
  <div id="leftBar">
    <!-- 收缩按钮 -->
    <el-radio-group id="close-bar-btn" v-model="isCollapse" style="position: absolute;">
      <el-radio-button :label="false"><i class="el-icon-d-arrow-right"></i></el-radio-button>
      <el-radio-button :label="true"><i class="el-icon-d-arrow-left"></i></el-radio-button>
    </el-radio-group>
    <!-- 菜单列表 -->
    <el-menu id="leftBarMain" default-active="1-4-1" class="el-menu-vertical-demo" @open="handleOpen" @close="handleClose" :collapse="isCollapse">
      <el-menu-item index="1">
        <i class="el-icon-menu"></i>
        <span slot="title">系统首页</span>
      </el-menu-item>
      <!-- 2 -->
      <el-submenu index="2">
        <template slot="title">
          <i class="el-icon-setting"></i>
          <span slot="title">借款管理</span>
        </template>
        <el-menu-item-group>
          <span slot="title">分组一</span>
          <el-menu-item index="1-1">选项1</el-menu-item>
          <el-menu-item index="1-2">选项2</el-menu-item>
        </el-menu-item-group>
        <el-menu-item-group title="分组2">
          <el-menu-item index="1-3">选项3</el-menu-item>
        </el-menu-item-group>
        <el-submenu index="1-4">
          <span slot="title">选项4</span>
          <el-menu-item index="1-4-1">选项1</el-menu-item>
        </el-submenu>
      </el-submenu>
      <!-- 3 -->
      <el-submenu index="3">
        <template slot="title">
          <i class="el-icon-setting"></i>
          <span slot="title">资金管理</span>
        </template>
        <el-menu-item-group>
          <span slot="title">分组一</span>
          <el-menu-item index="1-1">选项1</el-menu-item>
          <el-menu-item index="1-2">选项2</el-menu-item>
        </el-menu-item-group>
        <el-menu-item-group title="分组2">
          <el-menu-item index="1-3">选项3</el-menu-item>
        </el-menu-item-group>
        <el-submenu index="1-4">
          <span slot="title">选项4</span>
          <el-menu-item index="1-4-1">选项1</el-menu-item>
        </el-submenu>
      </el-submenu>
      <!-- 4 -->
      <el-menu-item index="4">
        <i class="el-icon-setting"></i>
        <span slot="title">认证管理</span>
      </el-menu-item>
      <!-- 5 -->      
      <el-menu-item index="5">
        <i class="el-icon-setting"></i>
        <span slot="title">用户管理</span>
      </el-menu-item>
      <!-- 6 -->
      <el-menu-item index="6">
        <i class="el-icon-setting"></i>
        <span slot="title">宣传管理</span>
      </el-menu-item>
      <!-- 7 -->
      <el-menu-item index="7">
        <i class="el-icon-setting"></i>
        <span slot="title">系统管理</span>
      </el-menu-item>
      <!-- 8 -->
      <el-menu-item index="8">
        <i class="el-icon-setting"></i>
        <span slot="title">统计模块</span>
      </el-menu-item>
      <!-- 9 -->
      <el-menu-item index="9">
        <i class="el-icon-setting"></i>
        <span slot="title">管理模块</span>
      </el-menu-item>
    </el-menu>
  </div>
</template>

<style>
  .el-menu-vertical-demo:not(.el-menu--collapse) {
    width: 200px;
  }
  .el-radio-button.is-active {
    display: none;
  }
  #close-bar-btn {
    z-index: 1;
  }
</style>

<script>
  export default {
    data() {
      return {
        isCollapse: false
      };
    },
    methods: {
      handleOpen(key, keyPath) {
        console.log(key, keyPath);
      },
      handleClose(key, keyPath) {
        console.log(key, keyPath);
      },
      setHeight(){
        let leftBarMain = document.getElementById('leftBarMain');;
        let browserHeight = window.innerHeight;
        console.log(browserHeight);
  	    return leftBarMain.style.height = browserHeight+'px';
      }
    },
    mounted(){
      // console.log('hi')
    }
  }
</script>