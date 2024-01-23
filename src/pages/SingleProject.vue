<template>
    <div>
        <h1>{{ project.title }}</h1>
        <img :src="`${store.imgPath}${project.image}`" :alt="project.title">
    </div>
</template>

<script>
import axios from 'axios';
import {store} from '../data/store';
    export default {
        name: 'SingleProject',
        data(){
            return{
                store,
                project: null
            }
        },
        methods:{
            getProjectData(){
                console.log(this.$route);
                axios.get(`${this.store.apiUrl}/projects/${this.$route.params.id}`).then((res)=>{
                    console.log(res.data)
                    if(res.data.results){
                        this.project = res.data.results
                    } else {
                        this.$router.push({name: 'not.found'})
                    }
                });
            }
        },
        created(){
            this.getProjectData()
        }
    }
</script>

<style lang="scss" scoped>

</style>