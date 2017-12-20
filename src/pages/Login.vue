<template>
  <div id="login-box">
    <div class="login">
      <div style="margin: 20px;text-align: center;">
        用户登录
      </div>
      <el-form :label-position="labelPosition" label-width="80px" :model="loginForm" :rules="rules" ref="loginForm" status-icon>
        <el-form-item label="用户名" prop="account">
          <el-input v-model.trim="loginForm.account" ref="account"></el-input>
        </el-form-item>
        <el-form-item label="密码" prop="password">
          <el-input type="password" auto-complete="off" v-model.trim="loginForm.password" ref="password"></el-input>
        </el-form-item>
        <el-form-item>
          <el-button type="primary" @click="isLogin('loginForm')">登录</el-button>
          <!-- <el-button type="primary" v-on:click="isLogin">立即创建</el-button> -->
          <el-button @click="resetForm('loginForm')">取消</el-button>
        </el-form-item>
      </el-form>
    </div>
  </div>
</template>

<script>
  import axios from 'axios'

  export default {
    data() {
      return {
        labelPosition: 'top',
        loginForm: {
          account: '',
          password: ''
        },
        rules: {
          account : [{
            required: true,
            message: '请输入用户名'
          }],
          password : [{
            required: true,
            message: '请输入密码'
          }]
        }
      };
    },
    methods: {
      // submitForm(formName) {
      //   this.$refs[formName].validate((valid) => {
      //     if (valid) {
      //       alert('submit!');
      //       this.$router.push({ path: 'main' }) 
      //     } else {
      //       console.log('error submit!!');
      //       return false;
      //     }
      //   });
      // },
      resetForm(formName) {
        this.$refs[formName].resetFields();
      },      
      isLogin: function(formName) {
        this.$refs[formName].validate((valid) => {
          if (valid) {
            // alert('submit!');
        
            // 获取已有账号密码
            axios.get('/api/login/getAccount')
              .then((response) => {
                // 响应成功回调
                // console.log(response)
                // let params = { 
                //   account : this.$refs.account.value,
                //   password : this.$refs.password.value
                // };
                // console.log(params)

                // // 创建一个账号密码
                // return axios.post('/api/login/createAccount',params);
                // console.log('成功创建账号')

              })
              .then((response) => {
                console.log(response)
                console.log('成功创建账号？')
                this.$router.push({ path: 'main' })  // 成功登录并跳转
              })
              .catch((reject) => {
                console.log(reject)
              });
            
          } else {
            console.log('error submit!!');
            return false;
          }
        });

      }
    }
  }
</script>

<style>
#login-box {
  background: url(../../static/img/loginBg.jpg) no-repeat center;
  background-size: cover;
  position: absolute;
  left: 0;
  right: 0;
  bottom: 0;
  top: 0;
} 
.login {
  width: 460px;
  margin: 0 auto;
  margin-top: 10%;
  padding: 20px 30px;
  background-color: #fff;
  border-radius: 5px;
  border: 1px solid #cccccc;
  box-shadow: 0 0 10px #cccccc;
}
</style>
