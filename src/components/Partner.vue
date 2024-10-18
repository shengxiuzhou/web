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
        <el-row justify="space-between" class="image-container" :space-between="20">
            <el-col v-for="(image, index) in firstCurImg" :key="index" :span="colSpan" class="image-col" >
                <el-image :src="image" class="image" :fit="fill"></el-image>
            </el-col>
        </el-row>
        <el-row  justify="space-between" class="image-container" :space-between="20">
            <el-col v-for="(image, index) in firstCurImg" :key="index" :span="colSpan" class="image-col">
                <el-image :src="image" class="image"></el-image>
            </el-col>
        </el-row>
    </el-row>
</template>
<script setup>
   import {ref, onMounted} from 'vue'
   const firstImgList = [
    'https://cultureexpo-prod-1302844417.cos.ap-guangzhou.myqcloud.com//images/web/home/hezuo-3dExhibition.jpg',
    'https://cultureexpo-prod-1302844417.cos.ap-guangzhou.myqcloud.com//images/web/home/hezuo%20(9).png',
    'https://cultureexpo-prod-1302844417.cos.ap-guangzhou.myqcloud.com//images/web/home/hezuo%20(14).png',
    'https://cultureexpo-prod-1302844417.cos.ap-guangzhou.myqcloud.com//images/web/home/hezuo%20(15).png',
    'https://cultureexpo-prod-1302844417.cos.ap-guangzhou.myqcloud.com//images/web/home/hezuo%20(16).png',
    'https://cultureexpo-prod-1302844417.cos.ap-guangzhou.myqcloud.com//images/web/home/%E5%BB%BA%E8%AE%BE%E9%93%B6%E8%A1%8C.png',
    'https://cultureexpo-prod-1302844417.cos.ap-guangzhou.myqcloud.com//images/web/home/hezuo (7).png',
    'https://cultureexpo-prod-1302844417.cos.ap-guangzhou.myqcloud.com//images/web/home/hezuo (8).png',
    'https://cultureexpo-prod-1302844417.cos.ap-guangzhou.myqcloud.com//images/web/home/hezuo (10).png',
    'https://cultureexpo-prod-1302844417.cos.ap-guangzhou.myqcloud.com//images/web/home/hezuo (11).png',
    'https://cultureexpo-prod-1302844417.cos.ap-guangzhou.myqcloud.com//images/web/home/hezuo-3dExhibition.jpg',
    'https://cultureexpo-prod-1302844417.cos.ap-guangzhou.myqcloud.com//images/web/home/hezuo%20(9).png',
    'https://cultureexpo-prod-1302844417.cos.ap-guangzhou.myqcloud.com//images/web/home/hezuo%20(14).png',
    'https://cultureexpo-prod-1302844417.cos.ap-guangzhou.myqcloud.com//images/web/home/hezuo%20(15).png',
    'https://cultureexpo-prod-1302844417.cos.ap-guangzhou.myqcloud.com//images/web/home/hezuo%20(16).png',
];
let imgCount = ref(5);
let firstCurImg = ref([]);
let colSpan  = ref(0);
let curIndex = ref(0);
const isMobile = ref (window.innerWidth <=1200);
if(isMobile) {
    imgCount.value = 3;
} else {
    imgCount.value = 5;
}
colSpan.value = Math.floor(24/imgCount.value);
firstCurImg.value = firstImgList.slice(curIndex.value,curIndex.value + imgCount.value);
console.log('curIndex.value',curIndex.value);    
console.log(firstCurImg.value);  
const slidePrev = () => {
    curIndex.value = curIndex.value - 1;
    if (curIndex.value <0) {
        curIndex.value = curIndex.value + 1;
        return;
    }
    firstCurImg.value = firstImgList.slice(curIndex.value*imgCount.value,curIndex.value*imgCount.value + imgCount.value);
    console.log('curIndex.value',curIndex.value); 
    console.log(firstCurImg);   
};
const slideNext = () => {
    curIndex.value = curIndex.value + 1;
    if (curIndex.value > (firstImgList.length/imgCount.value -1)) {
        curIndex.value = curIndex.value - 1;
        console.log('slideNext:curIndex.value',curIndex.value); 
        return;
    }
    firstCurImg.value = firstImgList.slice(curIndex.value*imgCount.value,curIndex.value*imgCount.value + imgCount.value);
    console.log('curIndex.value',curIndex.value); 
    console.log(firstCurImg);   
};
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
    width: 100%;
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