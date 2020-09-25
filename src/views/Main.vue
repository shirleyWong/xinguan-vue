<template>
  <el-container class="main_container">
    <el-header>
<!--      logo和项目名称-->
      <div class="left_box">
        <img src="../assets/img/avatar.gif" alt="">
        <span>新冠物资管理系统</span>
      </div>
<!--      用户登录展示的头像和下拉菜单-->
      <div class="right_box">
        <el-dropdown>
          <img src="../assets/img/avatar.gif" alt="">
          <el-dropdown-menu slot="dropdown">
            <el-dropdown-item icon="el-icon-house">系统首页</el-dropdown-item>
            <el-dropdown-item icon="el-icon-ship">交流讨论</el-dropdown-item>
            <el-dropdown-item icon="el-icon-switch-button">退出登录</el-dropdown-item>
          </el-dropdown-menu>
        </el-dropdown>
      </div>
    </el-header>
    <el-container>
      <el-aside :width="isCollapse?'60px':'200px'">
<!--        侧边栏展开收起折叠效果-->
        <div class="toggle_box" @click="toggleCollapse">|||</div>
        <el-menu
          default-active="2"
          class="el-menu-vertical-demo"
          background-color="#001529"
          text-color="#fff"
          active-text-color="#ffd04b"
          :collapse="isCollapse"
          :collapse-transition="false"
          :unique-opened="true">
          <el-submenu index="1">
            <template slot="title">
              <i class="el-icon-location"></i>
              <span>用户管理</span>
            </template>
            <el-menu-item index="1-1">
                <i class="el-icon-location"></i>
                <span>用户管理</span>
            </el-menu-item>
          </el-submenu>
          <el-submenu index="2">
            <template slot="title">
              <i class="el-icon-setting"></i>
              <span>系统管理</span>
            </template>
            <el-menu-item index="2-1">
              <i class="el-icon-setting"></i>
              <span>系统管理</span>
            </el-menu-item>
          </el-submenu>
        </el-menu>
      </el-aside>
      <el-main>Main</el-main>
    </el-container>
  </el-container>
</template>

<script>
export default {
  name: 'Main',
  data () {
    return {
      isCollapse: true
    }
  },
  methods: {
    toggleCollapse () {
      this.isCollapse = !this.isCollapse
    }
  }
}
</script>

<style lang="less" scoped>
.main_container {
  height:100%;
}
.el-header {
  background-color: #001529;
  display:flex;
  justify-content: space-between;
  color:white;
  padding-left: 0;
  align-items: center;
  font-size: 20px;
  .left_box{
    display: flex;
    align-items: center;
    img{
      width: 50px;
      height: 50px;
      margin:10px;
      border-radius: 50%;
    }
    span {
      margin-left: 10px;
    }
  }
  .right_box {
  .el-dropdown>img {
    width: 50px;
    height: 50px;
    margin: 10px;
    border-radius: 50%;
    background-size: contain;
    }

  }
}

.el-aside {
  background-color: #001529;
  .el-menu{
    border-right: none;
  }
  //展开收起
  .toggle_box{
    background-color: chartreuse;
    font-size: 15px;
    font-weight: bold;
    line-height: 24px;
    color:white;
    letter-spacing: 0.2em;
    text-align: center;
    cursor:pointer;
  }
}

.el-main {
  background-color: #E9EEF3;
  color: #333;
  text-align: center;
  line-height: 160px;
}

</style>
