<template>
  <div class="app-container documentation-container">
    <video id="mmedia" width="80%" src="@/assets/video/five-min.mp4" />
    <br>
    <input id="btn" type="button" value="播放" @click="play">
  </div>
</template>

<script>

export default {
  name: 'Documentation',
  components: {},
  data() {
    return {
    }
  },
  methods: {
    play() {
      const mmedia = document.getElementById('mmedia')
      if (mmedia.paused) {
        mmedia.play()
        this.value = '暂停'
      } else {
        mmedia.pause()
        this.value = '播放'
      }
    }
  }
}
</script>

<style lang="scss" scoped>
</style>
