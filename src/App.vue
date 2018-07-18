<template>
  <div id="app">
    <div class="flex-box hug-flip-demo">
      <hugCardFlip :flipOpts=flipOpts1></hugCardFlip>
    </div>
  </div>
</template>

<script>
import hugCardFlip from './components/hug-card-flip/hug-card-flip';

export default {
  name: 'App',
  data() {
    return {
      flipOpts1: {
        width: 200,
        height: 300,
        front: require('./common/images/IMG_20180709_102521.jpg'),
        back: require('./common/images/IMG_20180709_102526.jpg'),
        speed: 1.5,
        axis: 'centerX'
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
