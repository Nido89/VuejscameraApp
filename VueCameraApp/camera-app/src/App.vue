<template>
  <div id="app">
    <Camera v-on:takePicture="this.takePicture"/>
    <Frame />
    
  </div>
</template>

<script>

import Camera from './components/Camera';
import Frame from './components/Frame';
export default {
  name: 'App',
  components: {
    Camera,
    Frame
  },
  methods: {
    takePicture (){
        let ratio=(window.innerHeight < window.innerWidth) ? 16/9 : 9/16;
        const picture = document.querySelector("canvas");
        picture.width = (window.innerWidth > 1280)? window.innerWidth : 1280;
        picture.height = window.innerWidth/ratio;
        const ctx = picture.getContext("2d");
        ctx.imageSmoothingEnabled = true;
        ctx.imageSmoothingQuality = "high";
        ctx.drawImage(document.querySelector("video"),0,0,picture.width,picture.height);
    }
  }
}
</script>

<style lang="scss">
body {
  font-family: Verdana, Geneva, Tahoma, sans-serif;
  margin: 0;
  padding: 0;
  background-color: lightseagreen;

}
</style>
