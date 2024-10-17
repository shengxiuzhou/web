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
                      <p class="img-title-container"><span class="img-title">{{curItem.title}}</span></p>
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
                        <a :href="item.url">{{item.title}}</a>
                    </li>
                </ul>
            </el-col>
        </el-row>
    </el-row>
</template>

<script setup>
    import {ref,onMounted} from 'vue';
    import  axios from 'axios';

    let newsList = ref([]);
    let curIndex = 0;
    let curItem =  ref({'title': ''});
    /**
     * @description 拉取新闻列表
     */
    const getNews = () => {
        axios.get('./public/news.json').then((res)=> {
            const {code, data} = res.data;
            if (code == 0) {
                newsList.value = data;
                handleList();
            } else {
                alert('拉取数据失败');
            }
        }) ;
    };
    /**
     * @description 对数据进行按时间最新排序，并截取最新的四条数据
     */
    const handleList = () =>{
        let list = newsList.value;
        list.sort((b,a) => new Date(a.datetime)-new Date(b.datetime));
        list = list.slice(0,4);
        newsList.value = list;
        curItem.value = newsList.value[curIndex];
    };
    onMounted(()=> {
        getNews();
    });
</script>
<style scoped>
    .news-container {
        position:relative;
        top:-8.5rem;
        width:80%;
        margin:0 auto;
        border-radius: 0.3125rem;
        padding:1rem;
        background-color:#ffffff;
        box-shadow: 0 .375rem 1.25rem 0 rgba(34, 47, 71, .12);
    }
    .img-title-container {
        width: 100%;
        height:3.125rem;
        position:absolute;
        bottom:0.125rem;
        background-color: rgba(0,0,0,0.5);
        color: #ffffff;
        margin:0;
        display: flex;
        align-items: center;
        font-size:1rem;
    }
    .img-title-container .img-title {
        padding-left:1.25rem;
    }
    .video-container {
        width:2.5rem;
        height:2.5rem;
        border-radius:2.5rem;
        background-color:#3d71eb;
        border: 0.0625rem solid white;
        position:absolute;
        bottom:1.25rem;
        right:1.25rem;
        display: flex;
        justify-content: center;
        align-items: center;
        z-index:2;
    }
    .video-player {
        font-size:1.875rem;
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
        font-size: 1rem;
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