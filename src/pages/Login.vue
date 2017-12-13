<template>
  <div id="login-box">
    <div class="login">
      <div style="margin: 20px;text-align: center;">
        用户登录
      </div>
      <el-form :label-position="labelPosition" label-width="80px" :model="loginForm" :rules="rules" ref="loginForm" status-icon>
        <el-form-item label="用户名" prop="name">
          <el-input v-model="loginForm.name"></el-input>
        </el-form-item>
        <el-form-item label="密码" prop="password">
          <el-input type="password" auto-complete="off" v-model="loginForm.password"></el-input>
        </el-form-item>
        <el-form-item>
          <el-button type="primary" @click="submitForm('loginForm')">立即创建</el-button>
          <!-- <el-button type="primary" v-on:click="isLogin">立即创建</el-button> -->
          <el-button @click="resetForm('loginForm')">取消</el-button>
        </el-form-item>
      </el-form>
    </div>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        labelPosition: 'top',
        loginForm: {
          name: '',
          password: ''
        },
        rules: {
          name : [{
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
    computed: {
      user() {
        return this.$store.state.user
      }
    },
    methods: {
      submitForm(formName) {
        this.$refs[formName].validate((valid) => {
          if (valid) {
            alert('submit!');
            this.$router.push({ path: 'main' }) 
          } else {
            console.log('error submit!!');
            return false;
          }
        });
      },
      resetForm(formName) {
        this.$refs[formName].resetFields();
      },      
      isLogin: function() {
        this.$http.get('http://localhost:8080/users?username='+this.name+'&password='+this.pwd).then((response) => { 
          //这里在isLogin方法中先判断一下后台返回的是否为空值，如果不是然后提交后台返回的值。
          //注意这里是个难点，Vuex与Vue-Resource结合使用。 
          if(response.body != null & response.body.length > 0){ 
            this.$store.commit('isLogin',response.body[0]);
            this.name=''
            this.pwd= ''
            this.$router.push({ path: 'main' }) 
          }else{
            alert('请输入正确的用户名和密码！！！');
            this.name=''
            this.pwd= ''
          }
          
        }).then((error)=> this.error = error)
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
