<template>
    <div v-if="projects" id="main-container">
        
        <!-- navigation buttons to display corresponding filtered project lists-->
        <div class="" id="nav-container"  @click="$emit('menuShowing')">
    
          <div class="" id="dance-menu">
            <button class="button" type="button shadow-none" @click="displayProjectsInCategory('dance');">
              dance
            </button>
          </div>
    
          <div class="" id="video-menu">
            <button class="button" @click="displayProjectsInCategory('video')">
              video 
            </button>
          </div>

          <div class="" id="video-menu">
            <button class="button" @click="console.log(filteredProjects)">
              test 
            </button>
          </div>
        </div>
    
        <!-- project content -->
        <div class="projects-wrapper text-center">
    
          <div class="projects-container"  v-for="(project, index) in filteredProjects" :key="index">
    
            <div class="project">
    
              <div class="title" @click="showinfo(index)">
                <h2> {{project.title}}</h2>
              </div>
    
              <transition-group name="slide">
              <div  class="content-container " v-if="index == this.openProject" :key="index"  >
                <p> {{project.catTitle}} </p>
                <p> {{project.content}} </p>

                <div v-for="img in project.imgs" :key="img">
                    <p>{{img.id}} </p>
                    <img class="project-image" :src="'http://localhost:1337' + img.attributes.url" alt="">
                </div>
              </div>
              </transition-group>
            </div>


    
          </div>
        </div>
    </div>
</template>


<script>
export default {

  data(){
    return {
        projects: null,
        activeCategory: '',
        openStatus: false,
        openProject: undefined,
    }
  },

  mounted() {
    fetch("https://strapi-sqmn.onrender.com/api/projects?populate=*")
      .then(res => res.json())
      .then(data => this.projects = data.data)
      .catch(err => console.log(err.message))
  },

  computed: {
    filteredProjects: function(){
        let processedProjects = this.projects.map(object => ({
            id: object?.id, 
            title: object.attributes?.title,
            imgs: object.attributes?.images?.data,
            catTitle: object.attributes?.category?.data?.attributes?.title
            }));
            return processedProjects.filter(project => {return project.catTitle.match(this.activeCategory)});   
        },
  },

  methods: {
        displayProjectsInCategory(newCategory){
            this.activeCategory = newCategory;
            this.openStatus = true;
        },
        
        showinfo(index){
        if (this.openProject === index){
          this.openProject = null;
        } else this.openProject = index;
        }
    }
}
</script>


<style>


#nav-container {
  width: 100%;
  position: sticky;
  display: flex;
  flex-direction: row;
  justify-content: center;
  top: 0;
  height: 100%;
  text-align: center;
  margin: 0px;
  }

.button{
  font-size: 30px;
  font-weight: bold;
  text-transform: uppercase;
  color: rgb(104, 104, 104);
  font-family: "Lucida Console", Monaco, monospace;
  background: none;
  border: none;
  -webkit-text-stroke-width: 0.5px;
  -webkit-text-stroke-color: black;
}
.button:hover{
  -webkit-text-stroke-width: 0.5px;
  -webkit-text-stroke-color: rgb(184, 184, 184);
}
.button:focus{
  color: rgb(184, 184, 184);
}
.projects-container{
  height: 100%;
  width: 100vw;
  max-width: 100vw;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  align-items: center;
  font-family: "Lucida Console", Monaco, monospace;
  }

  .content-container{
    text-align: center;
  }
.title{
  -webkit-text-stroke-width: 0.2px;
  -webkit-text-stroke-color: rgb(184, 184, 184);
  }
.title:hover{
  cursor: pointer;
  color: rgb(184, 184, 184);
  -webkit-text-stroke-width: 0.5px;
  -webkit-text-stroke-color: rgb(0, 0, 0);
  }
.project{
  height: 100%;
  min-height: 15vh;
  display: grid;
  align-items: center;
}
.project-image{
  max-width: 85%;
  max-height: 90vh;
}


.slide-enter-from{
  height: 0%;
}
.slide-enter-to{
  height: 100%;
}
.slide-enter-active{
  transition: all 1s ease-in-out;
}
.slide-leave-from{
  height: 100%;
}
.slide-leave-to{
  height: 0px;
}

  </style>
