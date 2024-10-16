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
           :grid="{rows:2, fill:'row'}"
           loop
           :autoplay="{delay:1000}"
           @swiper="onSwiper"
            >
            <swiper-slide v-for="(image, index) in firstImgList" :key="index" class="slide-item" style="width:230px;margin:10px">
                <el-image class="image" :src="image" :fit="fit" />
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
    'https://cultureexpo-prod-1302844417.cos.ap-guangzhou.myqcloud.com//images/web/home/hezuo%20(16).png'
];
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
    height: 500px;
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
    width:20px;
    border-radius:20px;
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
   font-size:24px;
   color:gray;
}
.image {
    width: 230px;
    height:120px;
}
#slide {
    width: 100%;
    margin:0;
}
.slide-item {
    width: 230px;
    height:120px;
    margin: 0 20px;
}
.prev-btn {
    position: absolute;
    right:20px;
    bottom: 30px;
}

.carousel-left {
    position: absolute;
    top: 30%;
    right:50px;
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
    background-color: rgba(0, 0, 0, 0.8);
    color:#000;
}
.arrow {
    color: white;
    font-size:20px;
}
</style>