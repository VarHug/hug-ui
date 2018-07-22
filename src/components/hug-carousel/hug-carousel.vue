<template>
  <div class="hug-carousel-stage" ref="stage">
    <div class="prev-btn hug-carousel-btn" @click.stop="prevClickHandler">
      <i class="icon-arrow-left"></i>
    </div>
    <ul class="hug-carousel-container" ref="carouselContainer">
      <li class="hug-carousel-item" v-for="(img, index) in carouselOpts.imagese" :key="index" ref="carouselItem">
        <img class="hug-carousel-img" :src="img">
      </li>
    </ul>
    <div class="next-btn hug-carousel-btn" @click.stop="nextClickHandler">
      <i class="icon-arrow-right"></i>
    </div>
  </div>
</template>

<script type="text/ecmascript-6">
export default {
  props: {
    carouselOpts: {
      type: Object
    }
  },
  data() {
    return {
      containerR: 0,
      angle: 0
    };
  },
  mounted() {
    // 获取DOM元素
    // let stage = this.$refs.stage;
    let carouselItems = this.$refs.carouselItem;
    let carouselContainer = this.$refs.carouselContainer;
    // 计算属性
    let itemsLen = carouselItems.length;
    this.angle = 360 / itemsLen;
    let angle = this.angle;
    let r = 0;
    let width = this.carouselOpts.width;
    let height = this.carouselOpts.height;
    let translateZr = (width / 2) / Math.tan((angle / 2) * Math.PI / 180) + 20;
    // 设置属性
    // 动态设置carouselContainer大小防止旋转时双螺旋旋转
    carouselContainer.style.width = width + 'px';
    carouselContainer.style.height = height + 'px';
    carouselContainer.style.marginTop = -height / 2 + 'px';
    carouselContainer.style.marginLeft = -width / 2 + 'px';
    carouselItems.forEach((item) => {
      item.style.width = width + 'px';
      item.style.height = height + 'px';
      item.style.transform = `rotateY(${r}deg) translateZ(${translateZr}px)`;
      r += angle;
    });
  },
  methods: {
    prevClickHandler() {
      this.containerR += this.angle;
      this.$refs.carouselContainer.style.transform = `rotateY(${this.containerR}deg)`;
    },
    nextClickHandler() {
      this.containerR -= this.angle;
      this.$refs.carouselContainer.style.transform = `rotateY(${this.containerR}deg)`;
    }
  }
};
</script>

<style lang="stylus" rel="stylesheet/stylus">

.hug-carousel-stage
  position relative
  min-height 100px
  box-sizing content-box
  user-select none

  perspective 1000

  .hug-carousel-btn
    font-size 35px
    color #999
    cursor pointer

  .prev-btn
    position absolute
    top 50%
    left 0

  .next-btn
    position absolute
    top 50%
    right 0

  /.hug-carousel-container
    position absolute
    top 50%
    left 50%
    font-size 0

    transition transform 1s
    transform-style preserve-3d

    .hug-carousel-item
      position absolute
      bottom 0
      box-shadow 0 1px 3px rgba(0,0,0,.5)
      overflow hidden
      transition opacity 1s, transform 1s

      .hug-carousel-img
        max-width 100%

</style>
