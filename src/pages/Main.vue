<template>
  <div>
    <el-container>
      <el-header>
        <header-top></header-top>
      </el-header>
      <el-container>
        <div id="Left-bar-box">
          <left-bar></left-bar>
        </div>
        <el-container>
          <el-main>
            <div id="main-box">
              <Breadcrumb></Breadcrumb>
              <pagination></pagination>
            </div>
          </el-main>
          <el-footer>
            <footer-bottom></footer-bottom>
          </el-footer>
        </el-container>
      </el-container>
    </el-container>
  </div>
</template>

<script>
import HeaderTop from '../components/HeaderTop'
import FooterBottom from '../components/FooterBottom'
import LeftBar from '../components/LeftBar'
import Pagination from '../components/Pagination'
import Breadcrumb from '../components/Breadcrumb'

export default{
  components:{
    HeaderTop,
    FooterBottom,
    LeftBar,
    Pagination,
    Breadcrumb
  }
}
</script>

<style>  
  .el-header,.el-footer {
    height: auto!important;
  }
  .el-aside {
    background-color: #D3DCE6;
    color: #333;
    text-align: center;
    width: auto!important;
    line-height: 200px;
  }
  
  #Left-bar-box {
    width: auto!important;
  }

  .el-main {
    background-color: #e5e9f2;
    color: #333;
    text-align: center;
    line-height: 160px;
  }
  #main-box {
    padding: 20px;
    background-color: #fff;
  }
</style>