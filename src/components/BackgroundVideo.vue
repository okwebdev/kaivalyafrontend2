<template>

    <!-- <video v-if="active" autoplay muted loop id="myVideo">
        <source :src="video" type="video/mp4">
      </video> -->

    <!-- <video

    :key="src"
    :width="width"
    controls
  >
    <source
      :src="src"
      :type="type"
    >
  </video> -->


  <video autoplay muted loop id="myVideo">
    <source  src="../assets/video/kaivalya-background.mp4" type="video/mp4">
  </video>

  </template>
    
  <script>
    // import video from "kaivalyafrontend/src/assets/video/kaivalya-background.mp4"
    
    export default {
        data() { 
            return {
                // src:"https://player.vimeo.com/video/852067414",
                // video: video,
                active: true
            }
        },
        props:{ 
        }
    }
  </script>
    
  <style scoped lang="css">
    #myVideo {
        position: fixed;
        right: 0;
        bottom: 0;
        min-width: 100%;
        min-height: 100%;
      }
  </style>