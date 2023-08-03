<template>
  <div class="app-container" :class="{ grid: isGrid}">
    <div class="main">
      <MainLogo id="logo" @toggle="toggleSplash()"></MainLogo>


      <NavBar v-if="!splashStatus" id="nav-bar" @menuShowing="toggleSplash()"></NavBar>

      <transition>
       <BackgroundVideo class="background-video" v-if="splashStatus"></BackgroundVideo>
      </transition>
    </div>
  </div>

</template>

<script>
import NavBar from './components/NavBar.vue';
import MainLogo from "./components/MainLogo.vue";
import BackgroundVideo from './components/BackgroundVideo.vue';




export default {
  name: 'App',
  components: {
    MainLogo,
    BackgroundVideo,
    NavBar,
},

data(){
  return{
    splashStatus: true,
    isGrid: true,
  }
},
methods: {
  toggleSplash(){
    this.splashStatus = false;
    this.isGrid = false;
  }
}
}
</script>


<style>
body{
  max-width: 100vw;
}
#app{
  width: 100vw;
  max-width: 100vw;
}
.main{
  width: 100vw;
  max-width: 100vw;
}
.grid{
  display: grid;
  place-items: center;
}
.app-container{
  margin: 0px;
  height: 100vh;
  max-height: 100vh;
  max-width: 100vw;
  color: black;
}
.background-video {
  z-index: -1;
  opacity: 5;
}

.v-enter-active,
.v-leave-active {
  transition: opacity 0.5s ease;
}
.v-enter-from,
.v-leave-to {
  opacity: 0;
}

#nav-bar{
  position: sticky;
  top: 0;
  max-width: 100vw;
}
#logo{
  padding: 0px;
}
.blur{
  filter: blur(3rem);
}

</style>
