<template>
    <div>
        <main class="container">
            <h1>Project List</h1> 
            <div class="row">
                <div class="col-12 col-md-4 col-lg-3" v-for="project in store.projects" :key="project.id">
                    <ProjectCard :project="project"/>
                </div>
            </div>
            <nav class="d-flex justify-content-center align-items-center my-4">
                <ul class="pagination">
                    <li class="page-item" :class="{'disabled': currentPage === 1}">
                        <button class="page-link" :disabled="currentPage === 1" @click="getAllProjects(currentPage - 1)">Previous
                        </button>
                    </li>
                    <li class="page-item" v-for="n in lastPage">
                        <button class="page-link" @click="getAllProjects(n)">{{n}}</button>
                    </li> 
                    <li class="page-item" :class="{'disabled': currentPage === lastPage}">
                        <button class="page-link" :disabled="currentPage === lastPage" @click="getAllProjects(currentPage + 1)">Next
                        </button>
                    </li>   
                </ul>
            </nav>
        </main>
    </div>
</template>

<script>
import {store} from "../data/store";
import axios from "axios";
import ProjectCard from "../components/ProjectCard.vue";
    export default {
        name: 'AppProjects',
        components: {
            ProjectCard
        },
        data(){
            return {
                store,
                currentPage: 1,
                lastPage: null,
                total: 0          
            }
        },
        methods: {
            getAllProjects(pageNum){
                axios.get(`${this.store.apiBaseUrl}/projects`,{params: {page: pageNum}}).then((res)=>{
                    console.log(res.data);
                    this.store.projects = res.data.results.data;
                    this.currentPage = res.data.results.current_page;
                    this.lastPage = res.data.results.last_page;
                    this.total = res.data.results.total;
                }).catch((err)=>{
                    console.log('error', err);
                })
                   
                }
            },
            created() {
                this.getAllProjects();
            }
    }
</script>

<style lang="scss" scoped>

</style>