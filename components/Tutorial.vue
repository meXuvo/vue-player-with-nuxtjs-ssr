<template>
  <div>
    <div id="app">
      <div v-if="HLSCore" class="player-container">
          <!-- <vue-core-video-player  :src="currentMovie.src"></vue-core-video-player> -->
          <vue-core-video-player @loadedmetadata="loaded" :core="HLSCore" src="https://bitdash-a.akamaihd.net/content/sintel/hls/playlist.m3u8"></vue-core-video-player>
      </div>
      <div>
        <button type="button" class="mt-5 px-5 py-2 rounded bg-red-600" @click.prevent="goPlay">play</button>
      </div>
    </div>
  </div>
</template>

<script>
let pluginLib;
let events;
if(process.browser){
  pluginLib = require('@core-player/playcore-hls');
  events = require('vue-core-video-player')
}
export default {
  data () {
    return {
      HLSCore:null,
      videoEvent:null,
    }
  },
  mounted(){
    this.HLSCore = pluginLib.default
    this.videoEvent = events.EVENTS
    
  },
  methods:{
    loaded(){
      // this.goPlay()
    },
    goPlay(){
      const player = document.querySelector('video');
      player.play()
    }
  }
}
</script>

<style>
.vcp-layer.play-pause-layer{
  display:none !important;
}
</style>
