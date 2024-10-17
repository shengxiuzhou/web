<template>
    <el-row  class="partner-container">
        <el-row class="title-container" type="flex" justify="space-between" align="middle">
            <el-col :span="12">
                <h2  class="title">
                    合作伙伴
                </h2>
            </el-col>
            <el-col :span="2" class="more-partner" >
                <div class="carousel-left">
                    <el-button type="primary" class="arrow-container"><el-icon class="arrow" @click="slidePrev"><ArrowLeft /></el-icon></el-button>
                </div>
                <div class="carousel-right">
                    <el-button type="primary" class="arrow-container"><el-icon class="arrow" @click="slideNext"><ArrowRight /></el-icon></el-button>
                </div>
            </el-col>
        </el-row>
        <swiper
           :slides-per-view="6"
           :slides-per-group="6"
           :grid="{rows:2, fill:'row'}"
           :space-between="10"
           :autoplay="{delay:1000}"
           @swiper="onSwiper"
            >
            <swiper-slide v-for="(image, index) in firstImgList" :key="index" class="slide-item" style="width:14.375rem;margin:0.625rem">
                <el-image class="image" :src="image"  :fit="fit"/>
            </swiper-slide>
        </swiper>
    </el-row>
</template>
<script setup>
   import {ref, onMounted} from 'vue'
   import {Swiper, SwiperSlide} from 'swiper/vue'
   import 'swiper/swiper-bundle.css'
    const firstImgList = [
    'https://cultureexpo-prod-1302844417.cos.ap-guangzhou.myqcloud.com//images/web/home/hezuo-3dExhibition.jpg',
    'https://cultureexpo-prod-1302844417.cos.ap-guangzhou.myqcloud.com//images/web/home/hezuo%20(9).png',
    'https://cultureexpo-prod-1302844417.cos.ap-guangzhou.myqcloud.com//images/web/home/hezuo%20(14).png',
    'https://cultureexpo-prod-1302844417.cos.ap-guangzhou.myqcloud.com//images/web/home/hezuo%20(15).png',
    'https://cultureexpo-prod-1302844417.cos.ap-guangzhou.myqcloud.com//images/web/home/hezuo%20(16).png',
    'https://cultureexpo-prod-1302844417.cos.ap-guangzhou.myqcloud.com//images/web/home/hezuo-3dExhibition.jpg',
    'https://cultureexpo-prod-1302844417.cos.ap-guangzhou.myqcloud.com//images/web/home/hezuo%20(9).png',
    'https://cultureexpo-prod-1302844417.cos.ap-guangzhou.myqcloud.com//images/web/home/hezuo%20(14).png',
    'https://cultureexpo-prod-1302844417.cos.ap-guangzhou.myqcloud.com//images/web/home/hezuo%20(15).png',
    'https://cultureexpo-prod-1302844417.cos.ap-guangzhou.myqcloud.com//images/web/home/hezuo%20(16).png',
    // 'https://cultureexpo-prod-1302844417.cos.ap-guangzhou.myqcloud.com//images/web/home/%E5%BB%BA%E8%AE%BE%E9%93%B6%E8%A1%8C.png',
    // 'https://cultureexpo-prod-1302844417.cos.ap-guangzhou.myqcloud.com//images/web/home/hezuo (7).png',
    // 'https://cultureexpo-prod-1302844417.cos.ap-guangzhou.myqcloud.com//images/web/home/hezuo (8).png',
    // 'https://cultureexpo-prod-1302844417.cos.ap-guangzhou.myqcloud.com//images/web/home/hezuo (10).png',
    // 'https://cultureexpo-prod-1302844417.cos.ap-guangzhou.myqcloud.com//images/web/home/hezuo (11).png',
    // 'https://cultureexpo-prod-1302844417.cos.ap-guangzhou.myqcloud.com//images/web/home/hezuo (12).png',
    // 'https://cultureexpo-prod-1302844417.cos.ap-guangzhou.myqcloud.com//images/web/home/%E8%85%BE%E8%AE%AF.png',
    // 'https://cultureexpo-prod-1302844417.cos.ap-guangzhou.myqcloud.com//images/web/home/hezuo(18).png'
];
// 其他的图片链接：
   
  const fit='fill';
  const swiperInstance= ref(null);
  const onSwiper = (swiper) => {
    swiperInstance.value = swiper;
  };
  const slidePrev = () => {
    swiperInstance.value.slidePrev();
  };
  const slideNext = () => {
    swiperInstance.value.slideNext();
  };
  const changeParnter = () => {};
//   const curIndex = 0;
//   const nextSlide = () => {
//     curIndex = (curIndex + 1) % firstImgList.length;
//   }
//   onMounted(() => {
//     setInterval(() => {nextSlide}, 3000);
//   });
</script>

<style scoped>
.partner-container {
    width: 80%;
    margin:0 auto;
    height: 31.25rem;
}
.title-container {
    width:100%
}
.title {
    font-size: 2.75rem;
    line-height: 3.875rem;
    font-family: PingFangSC-Light, PingFang SC;
    font-weight: 300;
    color: #333;
}
.more-partner {
    text-align: right;
}
.arrow-container {
    width:1.25rem;
    border-radius:1.25rem;
    background:#fff;
    border:none;
}
.arrow-container:hover {
    background:rgba(0,0,0,0.5);
    border:none;
}
.arrow-container .arrow:hover {
    color:#fff;
}
.arrow {
   font-size:1.5rem;
   color:gray;
}
.image {
    width: 14.375rem;
    height:11.25rem;
}
#slide {
    width: 100%;
    margin:0;
}
.slide-item {
    width: 14.375rem;
    height:11.25rem;
    margin: 0 1.25rem;
}
.prev-btn {
    position: absolute;
    right:1.25rem;
    bottom: 1.875rem;
}

.carousel-left {
    position: absolute;
    top: 30%;
    right:3.125rem;
    z-index:1;
}

.carousel-right {
    position: absolute;
    top: 30%;
    right:0.625rem;
    z-index:1;
}
.arrow-container {
    width:1.25rem;
    border-radius:1.25rem;
    background-color: rgba(0, 0, 0, 0.2);
    border:none;
}
.arrow-container:hover {
    background-color: rgba(0, 0, 0, 0.8);
    color:#000;
}
.arrow {
    color: white;
    font-size:1.25rem;
}
.swiper-container {
    width: 100%;
    height:300px;
}
.swiper {
    display: flex;
}
.swiper-slide {
    display:flex;
    justify-content: center;
    align-items: center;
}
.swiper-slide img {
    width:100%;
    height:auto;
}
</style>