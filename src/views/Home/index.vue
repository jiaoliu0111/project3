<template>
 <div>
    <div class="swiperBox">
      <vue-particles
        color="#fff"
        :particleOpacity="0.7"
        :particlesNumber="60"
        shapeType="circle"
        :particleSize="4"
        linesColor="#fff"
        :linesWidth="1"
        :lineLinked="true"
        :lineOpacity="0.4"
        :linesDistance="150"
        :moveSpeed="2"
        :hoverEffect="true"
        hoverMode="grab"
        :clickEffect="true"
        clickMode="push"
        class="lizi"
      >
      </vue-particles>
      <swiper :options="swiperOption" ref="mySwiper">
        <swiper-slide v-for="item in swipes" :key="item.id">
          <img :src="item.picUrl" >
        </swiper-slide>
            <!-- Optional controls -->
        <div class="swiper-pagination"  slot="pagination"></div>
        <div class="swiper-button-prev" slot="button-prev"></div>
        <div class="swiper-button-next" slot="button-next"></div>
        <div class="swiper-scrollbar"   slot="scrollbar"></div>
      </swiper>
    </div>
  </div>
</template>
<script>
// import { swiper, swiperSlide } from 'vue-awesome-swiper'
export default {
  name: 'carrousel',
  // props: ['swipes'],
  data () {
    return {
      swipes: [
        // {id: 1, picUrl: '@/assets/images/banner1.jpg'},
        {id: 1, picUrl: '../../../static/images/banner1.jpg'},
        {id: 2, picUrl: '../../../static/images/banner2.jpg'},
        {id: 3, picUrl: '../../../static/images/banner3.jpg'}
      ],
      swiperOption: {
        autoplay: {
          disableOnInteraction: false, // 用户操作后是否禁止自动循环
          delay: 3000 // 自自动循环时间
        }, // 可选选项，自动滑动
        speed: 1500, // 切换速度，即slider自动滑动开始到结束的时间（单位ms）
        loop: true, // 循环切换
        grabCursor: true, // 设置为true时，鼠标覆盖Swiper时指针会变成手掌形状，拖动时指针会变成抓手形状
        // setWrapperSize: true, //Swiper使用flexbox布局(display: flex)，开启这个设定会在Wrapper上添加等于slides相加的宽或高，在对flexbox布局的支持不是很好的浏览器中可能需要用到。
        autoHeight: true, // 自动高度。设置为true时，wrapper和container会随着当前slide的高度而发生变化。
        scrollbar: '.swiper-scrollbar',
        mousewheelControl: true, // 设置为true时，能使用鼠标滚轮控制slide滑动
        observeParents: true, // 当改变swiper的样式（例如隐藏/显示）或者修改swiper的子元素时，自动初始化swiper
        pagination: {
          el: '.swiper-pagination',
          // type : 'progressbar', //分页器形状
          clickable: true // 点击分页器的指示点分页器会控制Swiper切换
        },
        navigation: { // 左右点击
          nextEl: '.swiper-button-next',
          prevEl: '.swiper-button-prev'
        }
      },
      computed: {
        swiper () {
          return this.$refs.mySwiper.swiper
        }
      }
    }
  }
}
</script>
<style scoped>
.swiperBox {
  width: 590px;
  height: 470px;
  border: 1px solid #ccc;
}
.swiperBox img {
  width: 590px;
  height: 470px;
}
.lizi {
  width: 530px;
  height: 450px;
  background:transparent;
  position: fixed;
  left: 30px;
  top: 0;
  z-index: 999;
}
</style>
