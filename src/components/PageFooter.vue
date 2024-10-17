<template>
  <div class="footer-container">
    <el-row class="footer-content" >
      <el-col :span="8">
        <el-row>
          <el-col :span="12" class="info-container">
              <el-row class="title">
                网站信息
              </el-row>
              <ul class="list">
                <li v-for="(item, index) in info" :key="index" class="list-item">
                  <a :href="item.url">{{item.desc}}</a>
                </li>
              </ul>
          </el-col>
          <el-col :span="12">
            <el-row class="title">
                联系我们
            </el-row>
            <ul class="list">
              <li v-for="(item, index) in contacts" :key="index" class="list-item">
                <span>{{item}}</span>
              </li>
            </ul>
          </el-col>
        </el-row>
      </el-col>
      <el-col :span="16">
        <el-row type="flex" justify="space-between" :gutter="20">
          <el-col :span="6" v-for="(item, index) in qrCodes " :key="index" :gutter="40">
              <el-image :src="item.url"></el-image>
              <div class="qr-title">{{item.name}}</div>
          </el-col>
          <el-col :span="6">
            <el-form
              ref="ruleFormRef"
              :model="ruleForm"
              status-icon
              :rules="rules"
              label-width="auto"
              class="form"
              inline
            >
              <h2>订阅</h2>
              <el-form-item label="邮箱" prop="email">
                <el-input v-model="ruleForm.email" type="email" autocomplete="off" placeholder="请输入您的邮箱"/>
              </el-form-item>
              <el-form-item>
                <el-button type="primary" @click="submitForm(ruleFormRef)">
                  提交
                </el-button>
              </el-form-item>
            </el-form>
          </el-col>
        </el-row>
      </el-col>
    </el-row>
    <el-row class="copyright" type="flex" align="middle">
      <el-col>
        Copyright © 2005-2025 中国（深圳）国际文化产业博览交易会 All Rights Reserved. 推荐使用 Chrome 浏览器或 Firefox 浏览器和1920*1080以上的分辨率，以获得最佳浏览效果.
      </el-col>
    </el-row>
    <el-row class="copyright"  type="flex" align="middle">
      <el-col>
        <span>ICP备案号：</span><a href="https://beian.miit.gov.cn/" class="copyright-text">粤ICP备14056205号</a>
        <img  src="https://www.cnicif.com/img/beiAnNum.d0289dc0.png"><a href="http://www.beian.gov.cn/portal/registerSystemInfo?recordcode=44030402005939">粤公网安备 44030402005939号</a>
      </el-col>
    </el-row>
  </div>
</template>

<script setup>
  import {ref} from 'vue'
  import {ElMessageBox} from 'element-plus'
  const info = [
    {desc: '关于我们',url:''},
    {desc: '官方声明',url:''},
    {desc: '隐私政策',url:''},
    {desc: '展会服务',url:''},
    {desc: '推荐服务商',url:''},
  ];
  const contacts = ['电话: 0755-83521188', '邮箱: wbh@cnicif.com', '地址: 深圳市福田区商报路奥林匹克大厦10楼', '大会服务: www.cnicif.com']; 
  const qrCodes = [
    {name: '文博会小程序',url:'https://cultureexpo-prod-1302844417.cos.ap-guangzhou.myqcloud.com/front/navigation/bg/footerTop_Minicode.jpg'},
    {name: '文博会订阅号',url:'https://cultureexpo-prod-1302844417.cos.ap-guangzhou.myqcloud.com/front/navigation/bg/footerTop_QRcode_new.png'},
    {name: '文博会抖音号',url:'https://cultureexpo-prod-1302844417.cos.ap-guangzhou.myqcloud.com/front/navigation/bg/footerTop_douyin.png'},
  ];
  const ruleForm = {
    email: '',
  };
  const rules = {
    email:[
      {required: true, message: '请输入您的邮箱',trigger: 'blur'},
    ] 
  };
  const ruleFormRef = ref(null);
  const submitForm = ()=> {
    ruleFormRef.value.validate((valid)=> {
      if(valid) {
        console.log('submit');
      } else {
        ElMessageBox.confirm('请输入您的邮箱','警告', {
          confirmButtonText: '确认',
          cancelButtonText: '取消',
          type:'warning'
        });
      }
    });
  };

</script>
<style scoped>
  .footer-container {
    background: url("https://www.cnicif.com/img/footer_bg_v2.3@2x.84ff0330.png") no-repeat 50%;
    background-size: 100% 100%;
    height: 42.01375rem;
  }
  .footer-content {
    padding: 5rem 2.5rem 5rem 6.25rem;
  }
  .info-container {
    padding-left: 2.5rem;
  }
  .title {
    font-size: 1.25rem;
    font-family: PingFangSC-Medium, PingFang SC;
    font-weight: 700;
    color: #333;
    line-height: 1.75rem;
  }
 .footer-content .list-item {
    max-width: 19.375rem;
    margin-top: 1.75rem;
    list-style-type:none;
  }
.list {
  padding:0;
}
  .list-item a {
    font-size: 1.125rem;
    font-family: PingFangSC-Regular, PingFang SC;
    font-weight: 400;
    color: #333;
    line-height: 1.5625rem;
  }
  .qr-title {
    text-align:center;
  }
  .copyright {
    text-align: center;
    color:rgb(147, 147, 147);
  }
  .copyright-text {
    padding-right: 0.625rem;
  }
  .form {
    padding:0.625rem;
    box-shadow: 0 .375rem 1.25rem 0 rgba(34, 47, 71, .12);
  }
</style>