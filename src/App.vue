<template>
  <div id="app">
    <div class="flex-box hug-flip-demo">
      <hugCardFlip :flipData=flipData></hugCardFlip>
    </div>
  </div>
</template>

<script>
import hugCardFlip from './components/hug-card-flip/hug-card-flip';

export default {
  name: 'App',
  data() {
    return {
      flipData: {
        width: 400,
        height: 600,
        front: require('./common/images/IMG_20180709_102521.jpg'),
        back: require('./common/images/IMG_20180709_102526.jpg')
      }
    };
  },
  components: {
    hugCardFlip
  }
};
</script>

<style lang="stylus" rel="stylesheet/stylus">
.flex-box
  display flex
</style>
