<template>
  <el-menu
    default-active="role"
    class="el-menu-vertical-demo"
    background-color="#545c64"
    text-color="#fff"
    active-text-color="#ffd04b"
    router
  >
    <el-submenu index="1">
      <template slot="title">
        <i class="el-icon-location"></i>
        <span>权限管理</span>
      </template>
       <el-menu-item index="/role">
           <i class="el-icon-setting"></i>
            <span slot="title">角色列表</span>
      </el-menu-item>
      <el-menu-item index="/menu">
           <i class="el-icon-setting"></i>
            <span slot="title">菜单列表</span>
      </el-menu-item>
      <el-menu-item index="/resource">
           <i class="el-icon-setting"></i>
            <span slot="title">资源列表</span>
      </el-menu-item>
    </el-submenu>
    <el-menu-item index="/course">
      <i class="el-icon-menu"></i>
      <span slot="title">课程管理</span>
    </el-menu-item>
    <el-menu-item index="/user">
      <i class="el-icon-document"></i>
      <span slot="title">用户管理</span>
    </el-menu-item>
   <el-submenu>
      <template slot="title">
        <i class="el-icon-location"></i>
        <span>广告管理</span>
      </template>
       <el-menu-item index="/advert">
           <i class="el-icon-setting"></i>
            <span slot="title">广告列表</span>
      </el-menu-item>
      <el-menu-item index="/advert-space">
           <i class="el-icon-setting"></i>
            <span slot="title">广告位列表</span>
      </el-menu-item>
    </el-submenu>
  </el-menu>
</template>

<script lang="ts">
import Vue from "vue";
export default Vue.extend({
  name: "AsideBar"
});
</script>

<style lang="scss" scoped>
.el-menu {
    height:100vh;
}
</style>
