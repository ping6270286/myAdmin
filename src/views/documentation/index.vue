<template>
  <div class="app-container documentation-container">
    <video src="@/assets/video/five-min.mp4" id='mmedia' width="640px" height="400px" style="background:black;"/>
      
    <input type="button" id="btn" @click="play" value="播放">
  </div>
</template>

<script>
export default {
    name: "Documentation",
    components: {},
    data() {
        return {
          mmedia: '',
        };
    },
    methods: {
      play() {
        if(mmedia.paused){// 播放
              mmedia.play();
              this.value = "暂停";
          }else{// 暂停
              mmedia.pause();
              this.value = "播放";
          }
      },
    },
    created() {
      this.mmedia = document.getElementById("mmedia");
    },
};
</script>

<style lang="scss" scoped>
</style>
