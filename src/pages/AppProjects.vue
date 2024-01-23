<template>
    <div>
        <main class="container">
            <h1>Project List</h1> 
            <div class="row">
                <div class="col-12 col-md-4 col-lg-3" v-for="project in store.projects" :key="project.id">

                </div>
            </div>
        </main>
    </div>
</template>

<script>
import {store} from "../data/store";
import axios from "axios";
import ProjectCard from "../components/ProjectCard";
    export default {
        name: 'AppProjects',
        components: {
            ProjectCard
        },
        data(){
            return{
                store
            }
        },
        methods: {
            getAllProjects(){
                axios.get(`${this.store.apiUrl}/projects`).then((res) =>{
                    console.log(res.data);
                    this.store.projects = res.data.results.data;
                    
                });
            }
        },
        created() {
            this.getAllProjects();
        }
    }
</script>

<style lang="scss" scoped>

</style>