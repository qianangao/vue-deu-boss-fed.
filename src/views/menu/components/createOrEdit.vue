<template>
    <el-card class="box-card">
        <div slot="header" class="clearfix">
            <span>{{isEdit ? '编辑菜单' : '添加菜单'}}</span>
        </div>
        <el-form ref="form" :model="form" label-width="80px">
            <el-form-item label="菜单名称" prop="name">
              <el-input v-model="form.name"></el-input>
            </el-form-item>
            <el-form-item label="菜单路径" prop="href">
              <el-input v-model="form.href"></el-input>
            </el-form-item>
            <el-form-item label="上级菜单" prop="parentId">
              <el-select v-model="form.parentId" placeholder="请选择上级菜单">
                <el-option label="无上级菜单" :value="-1"></el-option>
                <el-option :label="item.name" :value="item.id" v-for="item in parentMenuList" :key="item.id"></el-option>
              </el-select>
            </el-form-item>
            <el-form-item label="描述" prop="description">
                <el-input v-model="form.description"></el-input>
            </el-form-item>
            <el-form-item label="前端图标" prop="icon">
                <el-input v-model="form.icon"></el-input>
            </el-form-item>
            <el-form-item label="是否显示" prop="shown">
              <el-radio-group v-model="form.shown">
                <el-radio :label="true">是</el-radio>
                <el-radio :label="false">否</el-radio>
              </el-radio-group>
            </el-form-item>
            <el-form-item label="排序" prop="orderNum">
                <el-input-number :min="1" v-model="form.orderNum"></el-input-number>
            </el-form-item>
            <el-form-item>
              <el-button type="primary" @click="onSubmit">提交</el-button>
              <el-button v-if="!isEdit" @click="resetForm">重置</el-button>
              <el-button v-if="isEdit" @click="$router.push('/menu')">返回</el-button>
            </el-form-item>
          </el-form>
      </el-card>
  </template>
<script lang="ts">
import Vue from 'vue'
import { createOrUpdateMenu, getEditMenuInfo } from '@/services/menu.ts'
export default Vue.extend({
  name: 'CreateOrEdit',
  props: {
      isEdit: {
          type: Boolean,
          default: false
      }
  },
  data () {
    return {
      parentMenuList: [],
      form: {
        parentId: -1, // -1表示没有上级菜单
        name: 'aa',
        href: '',
        icon: '',
        orderNum: 0,
        description: '',
        shown: true
      }
    }
  },
  created () {
      this.getMenuInfo()
  },

  methods: {
     resetForm () {
         console.log('111');
        this.$refs.form.resetFields();
      },
      async getMenuInfo () {
        const { data } = await getEditMenuInfo(this.$route.params.id || -1)
        if (data.code === '000000') {
            this.parentMenuList = data.data.parentMenuList
            if (data.data.menuInfo) {
              this.form = data.data.menuInfo
            }
        }
      },
    async onSubmit () {
      const { data } = await createOrUpdateMenu(this.form)
      if (data.code === '000000') {
          this.$message.success('操作成功')
        //   this.$router.back()
        this.$router.push('/menu')
      } else {
        this.$message.error(data.mesg)
      }
    }
  }
})
</script>
<style lang="scss" scoped></style>
