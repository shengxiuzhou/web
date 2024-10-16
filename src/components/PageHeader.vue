<template>
    <div class="header-container">
        <div class="header-top">
            <div class="menu-container">
                <el-row type="flex" align="middle" :gutter="20">
                    <el-col :span="7" class="img-container">
                        <img src="https://cultureexpo-prod-1302844417.cos.ap-guangzhou.myqcloud.com//module/img/20230424/f668ed8d81dd4fb1b6541d7c532f77ba.png" alt="">
                    </el-col>
                    <el-col :span="8">
                        <el-menu
                            :default-active="activeIndex"
                            class="el-menu-list"
                            mode="horizontal"
                            :ellipsis="false"
                            @select="handleSelect"
                        >
                            <el-menu-item index="0">首页</el-menu-item>
                            <el-menu-item index="1">新闻</el-menu-item>
                            <el-menu-item index="2">展馆</el-menu-item>
                            <el-menu-item index="3">展商</el-menu-item>
                            <el-menu-item index="4">展品</el-menu-item>
                            <el-menu-item index="5">活动</el-menu-item>
                        </el-menu>
                    </el-col>
                    <el-col :span="4">
                        <el-input placeholder="请输入内容"></el-input>
                    </el-col>
                    <el-col :span="2">
                        <el-button type="primary">搜索</el-button>
                    </el-col>
                </el-row>
            </div>
        </div>
        <div class="carousel-left">
            <el-button type="primary" class="arrow-container"><el-icon class="arrow"><ArrowLeft /></el-icon></el-button>
        </div>
        <div class="carousel-right">
            <el-button type="primary" class="arrow-container"><el-icon class="arrow"><ArrowRight /></el-icon></el-button>
        </div>
        <div class="header-bottom">
            <News></News>
        </div>
    </div>
</template>

<script setup>
    import {ref,onMounted} from 'vue'
    import News from './News.vue'
    const activeIndex = ref(1)
    const handleSelect = (tab,event) => {console.log(tab, event)}
    onMounted(()=> {
        console.log('组件已经挂在啦');
    });
</script>
<style scoped>
.header-container {
    height: 900px;
    background:#f8faff;
}
.carousel-left {
    position: absolute;
    top: 30%;
    left:10px;
    z-index:1;
}

.carousel-right {
    position: absolute;
    top: 30%;
    right:10px;
    z-index:1;
}
.arrow-container {
    width:20px;
    border-radius:20px;
    background-color: rgba(0, 0, 0, 0.2);
    border:none;
}
.arrow-container:hover {
    background-color: rgba(255, 255, 255, 0.5);
}
.arrow {
    color: white;
    font-size:20px;
}
.header-top{
  width:100%;
  height: 51.875rem;
  background-image: url('https://cultureexpo-prod-1302844417.cos.ap-guangzhou.myqcloud.com//module/img/20240512/67646adb13b245bcbee1336d3a8495fc.png');
  background-size:cover;
  background-position: center;
  background-repeat: no-repeat;
}
.img-container {
    margin:14px 20px 14px 100px;
    
}
.menu-container {
    width:100%;
    height:100px;
}
.menu-container:after{
    content: "";
    position: absolute;
    z-index: 2;
    display: inline-block;
    width: 100%;
    height: .0625rem;
    background: #fff;
    opacity: .3;
}
.el-menu-list {
    background-color:none;
    border:none;
    height:90px;
}
.el-menu--horizontal>.el-menu-item {
    color:#ffffff;
    font-size: 16px;
}
.el-menu--horizontal>.el-menu-item:hover  {
    background-color: #ffffff;
    color: #000000;
}
.el-menu--horizontal.el-menu  {
    border:none;
}
.el-menu {
    background-color: rgba(0, 0, 0, 0);
}
</style>