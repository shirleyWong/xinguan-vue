<template>
<!--  登陆表单的容器-->
  <div class="login_container">
<!--    登陆区域-->
    <div class="login_box">
      <!--    头像-->
      <div class="avatar_box">
        <img src="../assets/img/avatar.gif" alt="">
      </div>
      <!--    表单-->
      <el-form :model="loginForm" :rules="loginRules" ref="loginForm" class="login_form">
        <el-form-item prop="username">
          <el-input v-model="loginForm.username"  prefix-icon="el-icon-user-solid"></el-input>
        </el-form-item>
        <el-form-item prop="password">
          <el-input v-model="loginForm.password"  prefix-icon="el-icon-lock"></el-input>
        </el-form-item>
        <el-form-item prop="verifycode" class="verifycode_box">
            <el-input v-model="loginForm.verifycode"  class="verifycode" placeholder="请输入验证码" prefix-icon="el-icon-mobile"></el-input>
            <img src="../assets/img/msUYTY.gif" alt="" class="verifycode_img">
        </el-form-item>
        <el-form-item class="login_btn">
          <el-button type="primary" @click="submitForm('loginForm')">登录</el-button>
          <el-button @click="resetForm('loginForm')">重置</el-button>
        </el-form-item>
      </el-form>
    </div>

  </div>
</template>

<script>
export default {
  name: 'Login',
  data () {
    return {
      loginForm: {
        username: '',
        password: '',
        verifycode: ''
      },
      loginRules: {
        username: [
          {
            required: true,
            message: '请输入用户名',
            trigger: 'blur'
          },
          {
            min: 2,
            max: 20,
            message: '长度在 2 到 20 个字符',
            trigger: 'blur'
          }
        ],
        password: [
          {
            required: true,
            message: '请输入密码,由字母和数字组成',
            trigger: 'blur'
          },
          {
            min: 8,
            max: 20,
            message: '长度在 8 到 20 个字符',
            trigger: 'blur'
          }
        ],
        verifycode: [
          {
            required: true,
            message: '请输入验证码',
            trigger: 'blur'
          }
        ]
      }
    }
  },
  methods: {
    submitForm (formName) {
      this.$refs[formName].validate((valid) => {
        if (valid) {
          this.$router.push('/main')
        } else {
          console.log('error submit!!')
          return false
        }
      })
    },
    resetForm (formName) {
      this.$refs[formName].resetFields()
    }
  }
}
</script>

<style lang="less" scoped>
.login_container{
  height: 100%;
  background-color: #2c3e50;
}
.login_box{
  width:450px;
  height:380px;
  background-color: white;
  border-radius: 5px;
  position: absolute;
  left: 50%;
  top:50%;
  transform: translate(-50%,-50%);
  .avatar_box{
    width:130px;
    height:130px;
    border:1px solid #eeeeee;
    border-radius: 50%;
    padding: 10px;
    box-shadow: 0 2px 12px 0 rgba(0,0,0,0.1);
    margin:-65px auto;
    background-color: white;
    img{
      width:130px;
      height: 130px;
      border-radius: 50%;
      background-color: #eeeeee;
    }
  }
  .login_form{
    position: absolute;
    bottom:0px;
    width:100%;
    padding:0px 20px;
    box-sizing: border-box;
    .login_btn{
      display:flex;
      justify-content: flex-end;
    }
    .verifycode_box{
      display: flex;
      .verifycode{
        width:80%;
        justify-content: left;
      }
      .verifycode_img{
        width: 20%;
        height: 30px;
        justify-content: flex-end;
      }
    }
  }
}
</style>
