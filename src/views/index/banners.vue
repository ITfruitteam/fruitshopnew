<template>
  <div class="q-pa-md" style="width: 90.5%;padding-left: 10.5%;">
    <q-carousel animated v-model="slide" navigation infinite autoplay transition-prev="slide-right"
      transition-next="slide-left">
      <q-carousel-slide  v-for="item in banners" :key="item.goods" :name='item.image'>
        <router-link :to="'/app/home/productDetail/'+item.goods" target = _blank> <img :src="item.image" height="100%" width="100%" alt="" /></router-link>
      </q-carousel-slide>
      <!-- <q-carousel-slide  v-for="item in banners" :key="item.goods" :name='item.image' :img-src="item.image" /> -->
      <!-- <router-link :to="'/app/home/productDetail/'+item.goods" target = _blank> <img :src="item.image" alt="" /></router-link> -->
    </q-carousel>
  </div>

</template>
<style>

</style>



<script>
  import {
    bannerGoods
  } from '../../api/api'

  export default {
    data() {

      return {
        slide: 'http://127.0.0.1:8000/media/banner/banner1.jpg',
        banners: []
      }

    },
    methods: {
      getBanner() {
        bannerGoods()
          .then((response) => {
            console.log(response)
            //跳转到首页页response.body面
            this.banners = response.data
          })
          .catch(function (error) {
            console.log(error);
          });
      }
    },
    created() {
      this.getBanner();
    }

  }

</script>
