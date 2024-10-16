<template>
    <el-row  class="news-container">
        <el-row type="flex" justify="space-between">
            <el-col :span=11>
                <el-row>
                    <el-col>
                        <el-image src="https://cultureexpo-prod-1302844417.cos.ap-guangzhou.myqcloud.com//module/img/20241012/6e15014658ac451bbe39f75e66bf8b48.png" fill="cover"></el-image>
                    </el-col>
                </el-row>
                <el-row>
                    <el-col>
                      <p class="img-title-container"><span class="img-title">{{curItem.name}}</span></p>
                    </el-col>
                </el-row>
                <el-row>
                    <el-col>
                        <div class="video-container">
                            <el-icon class="video-player"><CaretRight /></el-icon>
                        </div>
                    </el-col>
                </el-row>
            </el-col>
            <el-col :span=11>
                <div class="title">新闻资讯</div>
                <ul>
                    <li class="list" :key="index" v-for="(item ,index) in newsList">
                        <a :href="item.url">{{item.name}}</a>
                    </li>
                </ul>
            </el-col>
        </el-row>
    </el-row>
</template>

<script setup>
  import {ref,onMounted} from 'vue'

  const newsList = [
        {url:'www.baidu.com', name:"藏不住了！在深圳可以待一整天的小众书店分享→"},
        {url:'www.baidu.com', name:"两个博览会”在苏州启幕 展现中国体育新气象"},
        {url:'www.baidu.com', name:"当AI遇到大芬油画村 科技如何让艺术插上腾飞的翅膀？"},
        {url:'www.baidu.com', name:"新闻联播关注！深圳万架无人机升空有多震撼"},
        {url:'www.baidu.com', name:"数据出炉！来看深圳这个假期有多“火”🤩"},
    ];
    const curIndex = 0;
    const curItem = newsList[curIndex];
        
    onMounted(()=> {
        console.log('News组件');
    });
</script>
<style scoped>
    .news-container {
        position:relative;
        top:-180px;
        width:80%;
        margin:0 auto;
        border-radius: 5px;
        padding:15px;
        background-color:#ffffff;
        box-shadow: 0 .375rem 1.25rem 0 rgba(34, 47, 71, .12);
    }
    .img-title-container {
        width: 100%;
        height:50px;
        position:absolute;
        bottom:2px;
        background-color: rgba(0,0,0,0.5);
        color: #ffffff;
        margin:0;
        display: flex;
        align-items: center;
        font-size:16px;
    }
    .img-title-container .img-title {
        padding-left:20px;
    }
    .video-container {
        width:40px;
        height:40px;
        border-radius:40px;
        background-color:#3d71eb;
        border: 1px solid white;
        position:absolute;
        bottom:20px;
        right:20px;
        display: flex;
        justify-content: center;
        align-items: center;
        z-index:2;
    }
    .video-player {
        font-size:30px;
        color:white
    }
    .title {
        font-size: 2.75rem;
        line-height: 3.875rem;
        font-family: PingFangSC-Light, PingFang SC;
        font-weight: 300;
        color: #333;
    }
    .list {
        font-size: 1.5rem;
        font-family: PingFangSC-Medium, PingFang SC;
        font-weight: 500;
        color: #333;
        line-height: 3rem;
    }
    .list a {
        color:#333;
        text-decoration: none;
    }
    .list a:hover {
        color:#6491ee;
    }
</style>