<template>
    <div class="header-container">
        <div class="header-top">
            <swiper
                @swiper="initSwiper"
            >
                <swiper-slide v-for="(image,index) in banners" :key="index">
                    <el-image :src="image"></el-image>
                </swiper-slide>
            </swiper>
            <div class="menu-container">
                <el-row type="flex" align="middle" :gutter="10">
                    <el-col :span="7" class="img-container">
                        <img src="https://cultureexpo-prod-1302844417.cos.ap-guangzhou.myqcloud.com//module/img/20230424/f668ed8d81dd4fb1b6541d7c532f77ba.png" alt="">
                    </el-col>
                    <el-col :span="7">
                        <el-menu
                            :default-active="activeIndex"
                            :class="showPhone?'hidden-menu':'show-menu'"
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
                        <div class="input-box" >
                            <el-input placeholder="请输入内容" v-model="search" :class="showPhone?'hidden-search-input':'show-search-input'"></el-input>
                        </div>
                        
                    </el-col>
                    <el-col :span="2">
                        <el-button type="primary" @click="onSearch" :class="showPhone?'hidden-search-btn':'show-search-btn'">搜索</el-button>
                    </el-col>
                    <el-col :span="2">
                        <el-button type="primary" @click="toggleNav" :class="showPhone?'show-nav':'hidden-nav'">切换导航</el-button>
                    </el-col>
                </el-row>
            </div>
        </div>
        <div class="carousel-left">
            <el-button type="primary" class="arrow-container" @click="slidePrev"><el-icon class="arrow"><ArrowLeft /></el-icon></el-button>
        </div>
        <div class="carousel-right">
            <el-button type="primary" class="arrow-container" @click="slideNext"><el-icon class="arrow"><ArrowRight /></el-icon></el-button>
        </div>
        <div class="header-bottom">
            <News></News>
        </div>
    </div>
</template>

<script setup>
    import {ref,onMounted} from 'vue'
    import News from './News.vue'
    import {ElMessageBox} from 'element-plus'
    import {Swiper, SwiperSlide} from 'swiper/vue'

    const activeIndex = ref(1)
    const mySwiper = ref(null);
    const handleSelect = (tab,event) => {console.log(tab, event)}
   
    const initSwiper = (swiper)=> {
        mySwiper.value = swiper;
    }
    const banners = [
    'https://cultureexpo-prod-1302844417.cos.ap-guangzhou.myqcloud.com//module/img/20240512/67646adb13b245bcbee1336d3a8495fc.png',
    'https://cultureexpo-prod-1302844417.cos.ap-guangzhou.myqcloud.com//module/img/20240314/9cf5adfda624442790c5ee6bdeb6b88f.png'
    ];
    const slideNext = () => {
        if (mySwiper.value) {
            mySwiper.value.slideNext();
        }
    };
    const slidePrev = () => {
        if (mySwiper.value) {
            mySwiper.value.slidePrev();
        }
    };
    let showPhone = ref(true);
    const toggleNav = ()=> {
        showPhone.value = !showPhone.value;
    }
    const search = ref('');
    const onSearch = () => {
        if (!search.value) {
            ElMessageBox.confirm('请输入关键词', '提示', {
                confirmButtonText: '确定',
                cancelButtonText: '取消',
                type:'warning'
            });
            console.log('search end');
        }
    };
    window.onresize = () => {
        if (window.screen.availWidth > 1200) {
            showPhone.value = false;
        } else {
            // showPhone.value = true;
            // console.log('showPhone value',showPhone.value);
        }
    }
    onMounted(()=> {
        if (window.screen.availWidth > 1200) {
            showPhone.value = false;
        }
        console.log('组件已经挂在啦');
    });
</script>
<style scoped>
.header-container {
    height: 65rem;
    background:#f8faff;
}
.carousel-left {
    position: absolute;
    top: 50%;
    left:1.25rem;
    z-index:1;
}

.carousel-right {
    position: absolute;
    top: 50%;
    right:1.25rem;
    z-index:1;
}
.arrow-container {
    width:1.25rem;
    border-radius:1.25rem;
    background-color: rgba(0, 0, 0, 0.2);
    border:none;
}
.arrow-container:hover {
    background-color: rgba(255, 255, 255, 0.5);
}
.arrow {
    color: white;
    font-size:1.25rem;
}
.header-top{
  width:100%;
  height: 51.875rem;
  position: relative;
}
.img-container {
    margin:0  1.25rem 0 6.25rem;
    
}
.menu-container {
    width:100%;
    height:6.25rem;
    position: absolute;
    top:0;
    left:0;
    z-index:1;
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
.show-menu {
    background-color:none;
    border:none;
    height:5.625rem;
}
.el-menu--horizontal>.el-menu-item {
    color:#ffffff;
    font-size: 1rem;
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
.header-bottom {
    position: absolute;
    top: 47.5rem;
    z-index:1;
    left:0;
    right:0;
    bottom:0;
    margin: auto;
}
.show-nav {
    visibility: hidden;
}
.input-box {
    display: flex;
    align-items: center;
    justify-content: flex-end;
}
@media(max-width:1200px) {
    .show-menu,.show-search-input,.show-search-btn {
        visibility: visible;
    }
    .show-search-input {
        width:80%;
    }
    .hidden-menu,.hidden-search-input,.hidden-search-btn {
        visibility: hidden;
    }
    .show-nav {
        visibility: visible;
    }
    .header-bottom {
        top: 40rem;
    }
    .header-container {
        height: 56.25rem;
    }
}
@media(min-width: 1201px) {
    .hidden-nav {
        visibility: hidden;
    }
}
</style>