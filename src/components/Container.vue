<template>
  <div id="container" class="container">
      <h2>Proyectos</h2>
      <img src="https://avatars.githubusercontent.com/u/78506146?s=400&v=4" alt="foto git" width="50" class="image">
      <hr>
      <loading v-if="load"/>
      <div id="cards" v-for="project in projects" :key="project.id">
        <Card :html_url="project.html_url" 
            :name="project.name" 
            :description="project.description" 
            :author="project.owner.login" 
            :url="project.html_url" 
            :homepage="project.homepage" />
      </div>
  </div>
</template>

<script>
    import Card from "./Card"
import Loading from './Loading.vue';
    export default {
        data: () => ({
            projects: null,
            load: false
        }),
        components: {
            Card,
            Loading
        },
        mounted(){
            this.getProjects();
        },
        methods:{
            async getProjects(){
                this.load = true;
                const res = await fetch("https://api.github.com/users/wilca/repos");
                const data = await res.json();
                this.projects = data;
                this.load = false;
            }
        }
    }
</script>

<style scoped>
    #cards{
        display: flex;
        flex-wrap: wrap;
        justify-content: center;
    }
    .container{
        margin: 1rem;
        border: 1px solid #eee;
        padding: 7px;
        box-shadow: 1px 1px 4px #333;
        text-align: center;
    }
    .image{
        border-radius: 50%;
    }
</style>