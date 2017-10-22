<template>
    <div class="arttmpl">
        <!--面包屑导航-->
        <el-row>
            <el-col :span="24">
                <div class="abread bt-line">
                    <el-breadcrumb separator="/">
                        <el-breadcrumb-item :to="{ path: '/' }">首页</el-breadcrumb-item>
                        <el-breadcrumb-item>商品管理</el-breadcrumb-item>
                        <el-breadcrumb-item>商品列表</el-breadcrumb-item>
                    </el-breadcrumb>   
                </div> 
            </el-col>    
        </el-row>
        <div class="operation">
            <el-row>
                <el-col :span="5">
                    <el-button>新增</el-button>
                    <el-button>全选</el-button>
                    <el-button>删除</el-button>
                </el-col>
                <el-col :span="3" :offset="16">
                    <el-input
                        placeholder="请输入搜索内容"
                        icon="search"
                        v-model="input2"
                        :on-icon-click="handleIconClick">
                    </el-input>
                </el-col>
            </el-row>
        </div>
        <el-row>
            <el-col :span="24">
                <el-table :data="list" style="width: 100%" >
                    <el-table-column type="selection" width="80" @selection-change="getrows">
                    </el-table-column>
                    <el-table-column prop="title" label="标题">
                    </el-table-column>
                    <el-table-column prop="categoryname" label="所属类别" width="160">
                    </el-table-column>    
                    <el-table-column prop="name" label="发布人/发布时间" width="270">
                        <template scope="scope">
                            {{scope.row.user_name}} / {{scope.row.add_time}}
                        </template>
</el-table-column>
<el-table-column prop="name" label="属性" width="100">
    1111
</el-table-column>
<el-table-column prop="name" label="操作" width="90">
    <!--<el-button type="info">修改</el-button>-->
    <template scope="scope"><el-button type="success" size="mini">修改</el-button></template>
</el-table-column>
</el-table>
</el-col>
</el-row>
</div>
</template>
<script>
    export default {
        data() {
            return {
                input2: '',
                list: [

                ]
            }
        },
        created() {
            this.getlist();
        },
        methods: {
            getrows() {
                console.log(1111);
            },
            getlist() {
                // 1.0 获取url
                var url = '/admin/goods/getlist?pageIndex=1&pageSize=10&searchvalue=';
                this.$http.get(url).then(res => {
                    // 判断服务器返回的状态status
                    if (res.data.status == 1) {
                        this.$message.error(res.data.message);
                        return;
                    }
                    console.log(res.data.message);
                    // 正常逻辑的处理
                    this.list = res.data.message;
                });
            },
            handleIconClick() {

            }
        }
    }
</script>
<style scoped>

</style>