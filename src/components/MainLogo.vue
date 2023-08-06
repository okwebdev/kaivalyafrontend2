<template>
    <div @click="$emit('toggle')" class="" id="Logo-container">
  
        <!-- <div id="logo">
          <img :src="image"/>
        </div> -->
        
        <div class="mainlogo">
          <img src="../assets/img/kaivalya-name-min.png" alt="">
        </div>
    </div>
  </template>
    
  <script>
    // import image from "/Users/oscarkhan/repos/kaivalya_website/kaivalya_vue/src/assets/img/kaivalya-name-min.png"
    
    export default {
        // data: function () {
        //     return {
        //         image: image
        //     }
        // }
    }
  </script>
    
  <style scoped lang="css">
   
    #Logo-container{
      max-width: 100vw;
      display: flex;
      align-items: center;
    }
  
    img {
      max-width: 350px;
      
  
    }
    #logo{
      margin: 0px;
      display: flex;
      justify-content: center;
    }
  
  </style>
  