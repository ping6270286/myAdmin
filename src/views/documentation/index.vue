
<template>
  <div>
    <el-row :gutter="20">
      <el-col :span="6">
        <div class="grid-content bg-purple">
          <el-tree :data="data" :props="defaultProps" @node-click="handleNodeClick" />
        </div>
      </el-col>
      <el-col :span="18">
        <div class="grid-content bg-purple-video">
          <video-player ref="videoPlayer" class="demo video-player vjs-custom-skin" :playsinline="true" :options="playerOptions" />
        </div>
      </el-col>
    </el-row>
  </div>
</template>

<script>
export default {
  name: 'Documentation',
  components: {},
  data() {
    return {
      playerOptions: {
        // 播放速度
        playbackRates: [0.5, 1.0, 1.5, 2.0],
        // 如果true,浏览器准备好时开始回放。
        autoplay: false,
        // 默认情况下将会消除任何音频。
        muted: false,
        // 导致视频一结束就重新开始。
        loop: false,
        // 建议浏览器在<video>加载元素后是否应该开始下载视频数据。auto浏览器选择最佳行为,立即开始加载视频（如果浏览器支持）
        preload: 'auto',
        language: 'zh-CN',
        // 将播放器置于流畅模式，并在计算播放器的动态大小时使用该值。值应该代表一个比例 - 用冒号分隔的两个数字（例如"16:9"或"4:3"）
        aspectRatio: '16:9',
        // 当true时，Video.js player将拥有流体大小。换句话说，它将按比例缩放以适应其容器。
        fluid: true,
        sources: [
          {
            type: 'video/mp4',
            src: require('@/assets/video/demo1.mp4')
          }
        ],
        // 你的封面地址
        poster: '',
        notSupportedMessage: '此视频暂无法播放，请稍后再试',
        controlBar: {
          timeDivider: true,
          durationDisplay: true,
          remainingTimeDisplay: false,
          // 全屏按钮
          fullscreenToggle: true
        }
      },
      data: [
        {
          label: '一级 1',
          children: [
            {
              label: 'demo1',
              src: require('@/assets/video/demo1.mp4')
            }
          ]
        },
        {
          label: '一级 2',
          children: [
            {
              label: 'demo2',
              src: require('@/assets/video/demo2.mp4')
            },
            {
              label: 'demo3',
              src: require('@/assets/video/demo3.mp4')
            }
          ]
        },
        {
          label: '一级 3',
          children: [
            {
              label: '二级 3-1',
              children: [
                {
                  label: 'demo4',
                  src: require('@/assets/video/demo4.mp4')
                }
              ]
            },
            {
              label: '二级 3-2',
              children: [
                {
                  label: '三级 3-2-1'
                }
              ]
            }
          ]
        }
      ],
      defaultProps: {
        children: 'children',
        label: 'label'
      }
    }
  },
  computed: {
    player() {
      return this.$refs.videoPlayer.player
    }
  },
  methods: {
    handleNodeClick(data) {
      if (data.src) {
        this.$set(this.playerOptions.sources, 0, {
          type: 'video/mp4',
          src: data.src
        })
        this.player.muted(false)
      }
    }
  }
}
</script>

<style lang="scss" scoped>
.el-row {
    margin: 20px auto;
    &:last-child {
        margin-bottom: 0;
    }
}
.el-col {
    border-radius: 4px;
}
.bg-purple {
    background: #d3dce6;
}
.bg-purple-video {
    background: #fff;
}
.grid-content {
    border-radius: 4px;
    min-height: 600px;
}
.demo {
    width: 95%;
    border-radius: 4px;
    overflow: hidden;
    background: #fff;
    margin: 0 auto;
}
</style>
<style>
.el-tree {
    background: #d3dce6;
}
</style>
