<template>
    <div>
        <main class="container">
            <h1>Project List</h1> 
            <div></div>
        </main>
        
        <ul>
            <li v-for="project in $store.state.projects" :key="project.id">
            <router-link :to="{ name: 'single-project', params: {id: project.id} }" class="btn btn-primary">
                {{ project.title }}
            </router-link>
            </li>
        </ul>
    </div>
</template>

<script>
import {store} from "../store";
import axios from "axios";
    export default {
        name: 'AppProjects',
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