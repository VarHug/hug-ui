<template>
  <div class="hug-flip-container" ref="flipContainer" @click="cardFlip">
    <div class="hug-flipper" :class="flipAxis" ref="hugFlipper">
      <div class="hug-flip-front" ref="flipFront">
        <!-- 正面内容 -->
        <slot name="front" class="flip-slot"></slot>
      </div>
      <div class="hug-flip-back" ref="flipBack">
        <!-- 反面内容 -->
        <slot name="back" class="flip-slot"></slot>
      </div>
    </div>
  </div>
</template>

<script type="text/ecmascript-6">
export default {
  props: {
    flipOpts: {
      type: Object
    }
  },
  data() {
    return {
      flipData: {
        width: 0,
        height: 0,
        speed: 1,
        axis: 'centerX'
      },
      isInverse: false
    };
  },
  mounted() {
    // 参数处理
    Object.assign(this.flipData, this.flipOpts);
    // 获取DOM元素
    let flipContainer = this.$refs.flipContainer;
    let hugFlipper = this.$refs.hugFlipper;
    let flipFront = this.$refs.flipFront;
    let flipBack = this.$refs.flipBack;
    // 设置容器宽高
    flipContainer.style.width = this.flipData.width + 'px';
    flipContainer.style.height = this.flipData.height + 'px';
    // 设置动画时间
    hugFlipper.style.transition = `transform ${this.flipData.speed}s`;
    // 设置动画种类
    if (this.flipData.axis === 'centerX') {
      hugFlipper.style.transformOrigin = '50% 50% 0';
      flipFront.style.transform = 'rotateY(0deg)';
      flipBack.style.transform = 'rotateY(180deg)';
    } else if (this.flipData.axis === 'left') {
      hugFlipper.style.transformOrigin = '0 50% 0';
      flipFront.style.transform = 'rotateY(0deg)';
      flipBack.style.transform = 'rotateY(180deg)';
    } else if (this.flipData.axis === 'right') {
      flipFront.style.transform = 'rotateY(0deg)';
      flipBack.style.transform = 'rotateY(180deg)';
      hugFlipper.style.transformOrigin = '100% 50% 0';
    } else if (this.flipData.axis === 'centerY') {
      flipFront.style.transform = 'rotateX(0deg)';
      flipBack.style.transform = 'rotateX(180deg)';
      hugFlipper.style.transformOrigin = '50% 50% 0';
    } else if (this.flipData.axis === 'top') {
      flipFront.style.transform = 'rotateX(0deg)';
      flipBack.style.transform = 'rotateX(180deg)';
      hugFlipper.style.transformOrigin = '50% 0 0';
    } else if (this.flipData.axis === 'bottom') {
      flipFront.style.transform = 'rotateX(0deg)';
      flipBack.style.transform = 'rotateX(180deg)';
      hugFlipper.style.transformOrigin = '50% 100% 0';
    }
  },
  methods: {
    cardFlip() {
      this.isInverse = !this.isInverse;
    }
  },
  computed: {
    flipAxis() {
      return this.isInverse && this.flipData.axis;
    }
  }
};
</script>

<style lang="stylus" rel="stylesheet/stylus">
.hug-flip-container

  perspective 1000

  .hug-flipper
    position relative
    width 100%
    height 100%

    cursor pointer

    transform-style preserve-3d

    &.left
      transform translate(100%) rotateY(180deg)

    &.centerX
      transform rotateY(180deg)

    &.right
      transform translate(-100%) rotateY(180deg)

    &.centerY
      transform rotateX(180deg)

    &.top
      transform translateY(100%) rotateX(180deg)

    &.bottom
      transform translateY(-100%) rotateX(180deg)

    /.hug-flip-container .hug-flip-front, /.hug-flip-container .hug-flip-back
      position absolute
      top 0
      left 0
      width 100%
      height 100%

      backface-visibility hidden

      .flip-slot
        width 100%
        height 100%
</style>
