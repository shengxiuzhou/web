<template>
    <el-row  class="partner-container">
        <el-row class="title-container" type="flex" justify="space-between" align="middle">
            <el-col :span="12">
                <h2  class="title">
                    合作伙伴
                </h2>
            </el-col>
            <el-col :span="2" class="more-partner" >
                <el-button type="primary" class="arrow-container"><el-icon class="arrow"><ArrowRight /></el-icon></el-button>
            </el-col>
        </el-row>
        <el-row type="flex" justify="space-between">
            <el-col :span="4" v-for="(url,index) in firstImgList" :key="index" >
                <el-image class="small-image" :src="url" :fit="fit" />
            </el-col>
        </el-row>
        <el-row type="flex" justify="space-between">
            <el-col :span="4" v-for="(url,index) in secondImgList" :key="index" >
                <el-image class="small-image" :src="url" :fit="fit" />
            </el-col>
        </el-row>
    </el-row>
</template>
<script setup>
    const firstImgList = [
    'https://cultureexpo-prod-1302844417.cos.ap-guangzhou.myqcloud.com//images/web/home/hezuo-3dExhibition.jpg',
    'https://cultureexpo-prod-1302844417.cos.ap-guangzhou.myqcloud.com//images/web/home/hezuo%20(9).png',
    'https://cultureexpo-prod-1302844417.cos.ap-guangzhou.myqcloud.com//images/web/home/hezuo%20(14).png',
    'https://cultureexpo-prod-1302844417.cos.ap-guangzhou.myqcloud.com//images/web/home/hezuo%20(15).png',
    'https://cultureexpo-prod-1302844417.cos.ap-guangzhou.myqcloud.com//images/web/home/hezuo%20(16).png'
  ];
  const secondImgList = [
    'https://cultureexpo-prod-1302844417.cos.ap-guangzhou.myqcloud.com//images/web/home/hezuo-3dExhibition.jpg',
    'https://cultureexpo-prod-1302844417.cos.ap-guangzhou.myqcloud.com//images/web/home/hezuo%20(9).png',
    'https://cultureexpo-prod-1302844417.cos.ap-guangzhou.myqcloud.com//images/web/home/hezuo%20(14).png',
    'https://cultureexpo-prod-1302844417.cos.ap-guangzhou.myqcloud.com//images/web/home/hezuo%20(15).png',
    'https://cultureexpo-prod-1302844417.cos.ap-guangzhou.myqcloud.com//images/web/home/hezuo%20(16).png'
  ];
  const fit='fill';
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
.small-image {
    margin: 5px; 
    border-radius: 5px;
    width:110%;
}
</style>