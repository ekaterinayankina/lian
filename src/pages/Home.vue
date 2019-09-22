<template>
  <div class="Main">
    <Header/>
    <div class="home">
      <swiper :options="swiperOption">
        <swiper-slide v-for="(slide, index) in swiperSlides" :key="index">
          <div class="slide-container">
            <img :src="getPic(index+1)" :alt="slide"/>
            <div class="text-container">
              <p class="title"> {{slide.title}} </p>
              <p class="text tracking-in-expand"> {{slide.text}} </p>
            </div>
          </div>
        </swiper-slide>
        <div class="swiper-pagination" slot="pagination"></div>
        <div class="swiper-button swiper-button-prev" slot="button-prev"></div>
        <div class="swiper-button swiper-button-next" slot="button-next"></div>
      </swiper>
    </div>
    <Footer/>
  </div>
</template>

<script>
import Header from '../components/Header/Header'
import Footer from '../components/Footer/Footer'
import 'swiper/dist/css/swiper.css'
import { swiper, swiperSlide } from 'vue-awesome-swiper'

export default {
  components: {
    Header,
    Footer,
    swiper,
    swiperSlide
  },
  data: () => {
    return {
      swiperOption: {
        pagination: {
          el: '.swiper-pagination'
        },
        navigation: {
          nextEl: '.swiper-button-next',
          prevEl: '.swiper-button-prev'
        }
      },
      swiperSlides:
        [
          {
            title: 'Lian Creative Agency',
            text: 'Minimal Freelance Portfolio'
          },
          {
            title: 'Lian Creative Agency2',
            text: 'Minimal Freelance Portfolio2'
          }
        ]
    }
  },
  mounted () {
    setInterval(() => {
      if (this.swiperSlides.length < 2) {
        this.swiperSlides.push(this.swiperSlides.length + 1)
      }
    }, 3000)
  },
  methods: {
    getPic (index) {
      return require('./../assets/banner_' + index + '.png')
    }
  }
}
</script>

<style lang="scss">
@import "../assets/scss/_swiper-slider.scss";
.home {
  display: inline-block;
  width: 100%;
  height: 500px;
}
.swiper-container {
  height: 325px;
  width: 100%;
}
.slide-container {
  height: 100%;
  img {
    width: 100%;
    height: 100%;
  }
  .title {
    margin: 0;
    padding: 0 18px;
    text-transform: uppercase;
    font-weight: 100;
    font-size: 0.65em;
    letter-spacing: 2px;
    color: white;
    background-color: black;
  }
  .text {
    margin-top: 2em;
    text-transform: uppercase;
    font-weight: 300;
    font-size: 0.23em;
    letter-spacing: 0.45em;
  }
}
.text-container {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}

</style>
