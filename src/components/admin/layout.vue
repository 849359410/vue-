<template>
<div class="tmpl">
    <el-row>
        <!--左边菜单-->
        <el-col :span="leftcol"> 
            <img class="img" src="../../../static/images/logo.png" alt="">
            <div class="layout menu">
             <el-menu default-active="1-2" class="el-menu-vertical-demo" :collapse="iscollapse">
        <!--购物商城-->
      <el-submenu index="1">
        <template slot="title"><i class="el-icon-message"></i>购物商城</template>
<el-menu-item-group>
    <router-link to="/admin/goodslist">
        <el-menu-item index="1-1">内容管理</el-menu-item>
    </router-link>
    <el-menu-item index="1-2">类别管理</el-menu-item>
    <el-menu-item index="1-3">评论管理</el-menu-item>
</el-menu-item-group>
</el-submenu>
<!--订单管理-->
<el-submenu index="2">
    <template slot="title"><i class="el-icon-message"></i>订单管理</template>
    <el-menu-item-group>
        <el-menu-item index="2-1">订单管理</el-menu-item>
    </el-menu-item-group>

</el-submenu>
</el-menu>
</div>
</el-col>

<el-col :span="rightcol">
    <!--顶部区域-->
    <el-row>
        <el-col :span="24">
            <div class="topbg">
                <el-row>
                    <el-col :span="1">
                        <i class="layout el-icon-menu area" @click="showhide"></i>
                    </el-col>
                    <el-col :span="23">
                        <span>欢迎XXX登陆</span>
                        <el-dropdown split-button type="primary">
                            更多
                            <el-dropdown-menu slot="dropdown">
                                <el-dropdown-item>修改密码</el-dropdown-item>
                                <el-dropdown-item>注销登录</el-dropdown-item>
                            </el-dropdown-menu>
                        </el-dropdown>
                    </el-col>
                </el-row>
            </div>
        </el-col>
    </el-row>
    <!--内容区域-->
    <el-row>
        <el-col :span="24">
            <!--利用vue-router进行填充-->
            <router-view></router-view>
        </el-col>
    </el-row>
</el-col>
</el-row>

<!--<router-view></router-view>-->
</div>
</template>

<script>
    export default {
        data() {
            return {
                //这个属性控制el-menu菜单的展开和收缩
                iscollapse: false,
                //定义变量，
                leftcol: 4,
                rightcol: 20
            }
        },
        methods: {
            showhide() {
                this.iscollapse = !this.iscollapse;
                if (this.iscollapse) {
                    this.leftcol = 1;
                    this.rightcol = 23;
                } else {
                    this.leftcol = 4;
                    this.rightcol = 20;
                }
            }
        }
    }
</script>

<style scoped>
    .img {
        width: 100%;
    }
</style>