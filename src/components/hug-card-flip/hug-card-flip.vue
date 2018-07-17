<template>
  <div class="hug-flip-container" ref="flipContainer" @click="cardFlip">
    <div class="hug-flipper" :class="{'is-inverse':isInverse}">
      <div class="hug-flip-front">
        <!-- 正面内容 -->
        <div class="img-wrapper">
          <img :width=flipData.width :height=flipData.height :src=flipData.front>
        </div>
      </div>
      <div class="hug-flip-back">
        <!-- 反面内容 -->
        <div class="img-wrapper">
          <img :width=flipData.width :height=flipData.height :src=flipData.back>
        </div>
      </div>
    </div>
  </div>
</template>

<script type="text/ecmascript-6">
export default {
  props: {
    flipData: {
      type: Object
    }
  },
  data() {
    return {
      isInverse: false
    };
  },
  mounted() {
    let flipContainer = this.$refs.flipContainer;
    console.log(this.flipData);
    flipContainer.style.width = this.flipData.width + 'px';
    flipContainer.style.height = this.flipData.height + 'px';
  },
  methods: {
    cardFlip() {
      this.isInverse = !this.isInverse;
    }
  },
  components: {

  }
};
</script>

<style lang="stylus" rel="stylesheet/stylus">
.hug-flip-container
  margin 0 auto

  perspective 1000

  .hug-flipper
    position relative
    width 100%
    height 100%

    cursor pointer

    transform-style preserve-3d
    transition transform 1.5s

    transform-origin 0 50% 0

    &.is-inverse
      transform translate(100%) rotateY(180deg)

    /.hug-flip-container .hug-flip-front, /.hug-flip-container .hug-flip-back
      position absolute
      top 0
      left 0
      width 100%
      height 100%

      backface-visibility hidden

    /.hug-flip-container .hug-flip-front
      transform rotateY(0deg)
    /.hug-flip-container .hug-flip-back
      transform rotateY(180deg)
</style>
