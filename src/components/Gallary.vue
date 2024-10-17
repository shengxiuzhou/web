<template>
    <el-row class="gallary-container">
        <el-row class="title-container">
            <el-col :span="22" >
                <h2 class="title"> 
                    推荐展馆
                </h2>
            </el-col>
            <el-col :span="2" class="more-gallary">更多展馆</el-col>
        </el-row>
        <el-row>
            <el-col :span="12">
                <el-row>
                    <el-col>
                        <div class="img-container">
                            <el-image class="big-image"  :src="largeImgUrl" :fit="fit" />
                            <div class="mask"></div>
                        </div>
                    </el-col>
                </el-row>

            </el-col>
            <el-col :span="12">
                <el-image class="small-image" :src="url" :fit="fit" v-for="(url,index) in smallImgUrl" :key="index" />
            </el-col>
        </el-row>
    </el-row>
</template>
<script setup>
  const largeImgUrl = 'https://cultureexpo-prod-1302844417.cos.ap-guangzhou.myqcloud.com//module/img/20230424/2b042e0aea27461888e414872f708a2d.png';
  const smallImgUrl = [
    'https://cultureexpo-prod-1302844417.cos.ap-guangzhou.myqcloud.com//module/img/20240325/6d139e31d3464210bfb5c171e2458198.png',
    'https://cultureexpo-prod-1302844417.cos.ap-guangzhou.myqcloud.com//module/img/20230424/60ad11746e974e00a4ac39ccca12f4ad.png',
    'https://cultureexpo-prod-1302844417.cos.ap-guangzhou.myqcloud.com//module/img/20230424/c2d63e5805a1444295ed745dc935e643.png',
    'https://cultureexpo-prod-1302844417.cos.ap-guangzhou.myqcloud.com//module/img/20230424/ee78461226c1465093260dd279fe0576.png'
  ];
  const fit='fill';
</script>

<style scoped>
.gallary-container {
    width: 80%;
    margin:0 auto;
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
.more-gallary {
    text-align:right;
}
.img-container {
    width: 98%; 
    height: 92%;
    position: relative;
    border-radius: 0.3125rem;
    margin: 0.3125rem; 
}
.big-image {
    width: 100%; 
    height: 100%;
    border-radius: 0.3125rem;
}
.mask {
    position:absolute;
    top:0;
    bottom:0;
    width:100%;
    height:100%;
    background-color: rgba(0,0,0,0.5);
    color: #fff;
    opacity:0;
    transition: opacity 0.3s ease;
}
.img-container:hover .mask {
    opacity: 1;
}
.small-image {
    width: 45%; 
    height: 45%; 
    margin: 0.3125rem; 
    border-radius: 0.3125rem;
}
</style>