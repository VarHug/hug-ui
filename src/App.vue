<template>
  <div id="app">
    <!-- <div class="hug-flip-demo">
      <hugCardFlip :flipOpts=flipOpts1>
        <div class="img-wrapper" slot="front">
          <img width="200" height="300" src="./common/images/IMG_20180709_102521.jpg">
        </div>
        <div slot="back">
          这是反面的内容插槽
        </div>
      </hugCardFlip>
      <hugCardFlip :flipOpts=flipOpts2>
        <div class="front-wrapper" slot="front">
          <div class="img-wrapper">
            <img width="400" height="600" src="./common/images/IMG_20180709_102521.jpg">
          </div>
          <h2 class="flip-title">Saber Cosplay Front</h2>
        </div>
        <div class="front-wrapper" slot="back">
          <div class="img-wrapper">
            <img width="400" height="600" src="./common/images/IMG_20180709_102526.jpg">
          </div>
          <h2 class="flip-title">Saber Cosplay Back</h2>
        </div>
      </hugCardFlip>
    </div> -->
    <div class="hug-carousel-demo">
      <hugCarousel class="carousel" :carouselOpts=carouselOpts>
      </hugCarousel>
      <hugCarousel class="carousel" :carouselOpts=carouselOpts2>
      </hugCarousel>
    </div>
  </div>
</template>

<script>
import hugCardFlip from './components/hug-card-flip/hug-card-flip';
import hugCarousel from './components/hug-carousel/hug-carousel.vue';

export default {
  name: 'App',
  data() {
    return {
      flipOpts1: {
        width: 200,
        height: 300,
        speed: 1.5,
        axis: 'centerX'
      },
      flipOpts2: {
        width: 400,
        height: 650,
        speed: 1,
        axis: 'left'
      },
      carouselOpts: {
        width: 240,
        height: 160,
        data: [{
            link: 'https://xxxxxx.com',
            image: require('./common/images/3x2_1.jpg')
          }, {
            link: 'https://xxxxxx.com',
            image: require('./common/images/3x2_2.jpg')
          }, {
            link: 'https://xxxxxx.com',
            image: require('./common/images/3x2_3.jpg')
          }, {
            link: 'https://xxxxxx.com',
            image: require('./common/images/3x2_4.jpg')
          }, {
            link: 'https://xxxxxx.com',
            image: require('./common/images/3x2_5.jpg')
          }, {
            link: 'https://xxxxxx.com',
            image: require('./common/images/3x2_6.jpg')
          }, {
            link: 'https://xxxxxx.com',
            image: require('./common/images/3x2_7.jpg')
          }, {
            link: 'https://xxxxxx.com',
            image: require('./common/images/3x2_8.jpg')
          }, {
            link: 'https://xxxxxx.com',
            image: require('./common/images/3x2_9.jpg')
          }
        ]
      },
      carouselOpts2: {
        width: 150,
        height: 100,
        data: [{
            link: 'https://xxxxxx.com',
            image: require('./common/images/3x2_1.jpg')
          }, {
            link: 'https://xxxxxx.com',
            image: require('./common/images/3x2_2.jpg')
          }, {
            link: 'https://xxxxxx.com',
            image: require('./common/images/3x2_3.jpg')
          }, {
            link: 'https://xxxxxx.com',
            image: require('./common/images/3x2_4.jpg')
          }, {
            link: 'https://xxxxxx.com',
            image: require('./common/images/3x2_5.jpg')
          }, {
            link: 'https://xxxxxx.com',
            image: require('./common/images/3x2_6.jpg')
          }
        ]
      }
    };
  },
  components: {
    hugCardFlip,
    hugCarousel
  }
};
</script>

<style lang="stylus" rel="stylesheet/stylus">
.hug-flip-demo
  display flex
  > div
    margin 0 auto

.img-wrapper
  font-size 0
.flip-title
  text-align center
  margin-top 20px
  font-size 20px
  font-weight 700
  color #a7a0a2

.carousel
  width 700px
  height 300px
  padding 100px 50px
  margin 0 auto

.carousel:nth-child(2)
  width 500px

</style>
