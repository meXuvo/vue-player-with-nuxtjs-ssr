<template>
  <div>
    <div id="app">
      <div v-if="HLSCore" class="player-container">
          <vue-core-video-player :core="HLSCore" src="https://bitdash-a.akamaihd.net/content/sintel/hls/playlist.m3u8"></vue-core-video-player>
      </div>
    </div>
  </div>
</template>

<script>
let pluginLib;
if(process.browser){
  pluginLib = require('@core-player/playcore-hls');
}
export default {
  data () {
    return {
      HLSCore:null,
    }
  },
  mounted(){
    this.HLSCore = pluginLib.default
  }
}
</script>

<style>
.vcp-layer.play-pause-layer{
  display:none !important;
}
</style>
