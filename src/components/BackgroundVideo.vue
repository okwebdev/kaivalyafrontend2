<template>

    <video v-if="active" autoplay muted loop id="myVideo">
        <source :src="video" type="video/mp4">
      </video>

  </template>
    
  <script>
    import video from "/Users/oscarkhan/repos/kaivalya_website/kaivalya_vue/src/assets/video/kaivalya-background.mp4"
    
    export default {
        data() { 
            return {
                video: video,
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