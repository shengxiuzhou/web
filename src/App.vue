<script setup>
import { RouterLink, RouterView } from 'vue-router'
import PageHeader from './components/PageHeader.vue'
import PageBody from './components/PageBody.vue'
import PageFooter from './components/PageFooter.vue'
</script>

<template>
  <div>    
    <PageHeader></PageHeader>
    <PageBody></PageBody>
    <PageFooter></PageFooter>
  </div> 
  <!-- <header>
    <img alt="Vue logo" class="logo" src="@/assets/logo.svg" width="125" height="125" />

    <div class="wrapper">
      <HelloWorld msg="You did it!" />

      <nav>
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/about">About</RouterLink>
      </nav>
    </div>
  </header>

  <RouterView /> -->
</template>

<style scoped>

</style>
