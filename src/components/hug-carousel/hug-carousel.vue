<template>
  <div class="hug-carousel-stage" ref="stage" v-if="showFlag">
    <div class="prev-btn hug-carousel-btn" @click.stop="prevClickHandler">
      <i class="icon-arrow-left"></i>
    </div>
    <ul class="hug-carousel-container" ref="carouselContainer">
      <li class="hug-carousel-item" v-for="(data, index) in carouselOpts.data" :key="index" ref="carouselItem" @click.stop="itemClickHandler(index)">
        <img class="hug-carousel-img" :src="data.image" :key="index">
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
      showFlag: false,
      containerR: 0,
      angle: 0,
      curIndex: 0,
      itemsLen: 0
    };
  },
  created() {
    let opts = this.carouselOpts;
    if (opts && opts.width && opts.height && opts.data.image) {
      this.showFlag = true;
    }
  },
  mounted() {
    if (this.showFlag) {
      // 获取DOM元素
      // let stage = this.$refs.stage;
      let carouselItems = this.$refs.carouselItem;
      let carouselContainer = this.$refs.carouselContainer;
      // 计算属性
      let itemsLen = carouselItems.length;
      this.itemsLen = itemsLen;
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
    }
  },
  methods: {
    prevClickHandler() {
      this.curIndex--;
      if (this.curIndex < 0) {
        this.curIndex = this.itemsLen - 1;
      }
      this.containerR += this.angle;
      this.$refs.carouselContainer.style.transform = `rotateY(${this.containerR}deg)`;
    },
    nextClickHandler() {
      this.curIndex = ++this.curIndex % this.itemsLen;
      this.containerR -= this.angle;
      this.$refs.carouselContainer.style.transform = `rotateY(${this.containerR}deg)`;
    },
    itemClickHandler(index) {
      if (index === this.curIndex) {
        if (this.carouselOpts.data[index].link) {
          window.open(this.carouselOpts.data[index].link);
        }
      } else {
        let diff = index - this.curIndex;
        if ((diff > 0 && diff < this.itemsLen / 2) || diff < -this.itemsLen / 2) {
          // 顺时针转
          if (diff < 0) {
            diff = this.itemsLen - Math.abs(diff);
          }
          this.containerR -= this.angle * diff;
        } else {
          // 逆时针转
          if (diff < 0) {
            diff = Math.abs(diff);
          } else {
            diff = this.itemsLen - diff;
          }
          this.containerR += this.angle * diff;
        }
        this.curIndex = index;
        this.$refs.carouselContainer.style.transform = `rotateY(${this.containerR}deg)`;
      }
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
    position absolute
    top 50%
    padding 5px
    z-index 100
    font-size 30px
    color hsla(0,0%,100%,.4)
    background-color rgba(0,0,0,.2)
    cursor pointer
    transform translate(0, -50%)
    &:hover
      color hsla(0,0%,100%,.6)
      background-color rgba(0,0,0,.4)

  .prev-btn
    left 0

  .next-btn
    right 0

  /.hug-carousel-container
    position absolute
    top 50%
    left 50%
    font-size 0

    transition transform 1s
    transform-style preserve-3d

    /.hug-carousel-item
      position absolute
      bottom 0
      cursor pointer
      box-shadow 0 1px 3px rgba(0,0,0,.5)
      overflow hidden
      transition opacity 1s, transform 1s

        /.hug-carousel-img
          display 100%
          max-width 100%
</style>
