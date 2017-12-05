<template>
  <div id="headerTop">
    <!-- logo -->
    <div class="logo"><img src="../../static/img/logo.png" alt="LOGO">LOGO</div>

    <!-- 下拉菜单 -->
    <el-dropdown class="chooseBox">
      <span class="el-dropdown-link">
        <img src="../../static/img/headImg.png" alt="用户头像" id="headImg"> 显示用户名<i class="el-icon-arrow-down el-icon--right"></i>
      </span>
      <el-dropdown-menu slot="dropdown" class="chooseItem">
        <el-dropdown-item>个人设置</el-dropdown-item>
        <el-dropdown-item disabled>系统设置</el-dropdown-item>
        <el-dropdown-item divided>退出</el-dropdown-item>
      </el-dropdown-menu>
    </el-dropdown>
    
    <!-- 系统消息 -->
    <el-badge :value="120" :max="99" class="item" id="sysInfo">
      <el-button size="small"><i class="el-icon-message"></i> 消息</el-button>      
    </el-badge>
    

  </div>
</template>

<style>
#headerTop {
  background-color: #324057;
  margin: 0 -20px;
  padding: 20px;
  overflow: hidden;
}
.logo {
  float: left;
  color: #cbcfd4;
  line-height: 38px;
}
#headerTop img {
  vertical-align: middle;
}
.chooseBox {
  float: right;
}
.chooseBox .el-dropdown-link {
  color: #ffffff;
  line-height: 38px;
}
.chooseItem {
  text-align: center;
}
#headImg {
  border-radius: 50%;
  width: 38px;
  height: 38px;
}
#sysInfo {
  float: right;
  line-height: 38px;
  margin-right: 50px;
}
</style>
