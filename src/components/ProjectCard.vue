<template>
    <div class="card">
        <img :src="`${store.imgPath}${post.image}`" class="card-img-top" alt="...">
        <div class="card-body">
            <h5 class="card-title">{{ truncateTitle }}</h5>
            <p class="card-text">{{ truncateBody }}</p>
            <router-link :to="{ name: 'single-project', params: {id: project.id} }" class="btn btn-primary">
                    {{ project.title }}
            </router-link>
        </div>
    </div>
</template>

<script>
import {store} from "../data/store";
    export default {
        name: 'ProjectCard',
        props: ['project'],
        data(){
            return{
                store,
                titleMaxLen: 25,
                bodyMaxLen: 100,
            }
        },
        computed:{
            truncateTitle(){
                if(this.project.title.length > this.titleMaxLen){
                    return this.project.title.substr(0,this.titleMaxLen) + '...';
                }
                return this.post.title;            
            },
            truncateBody(){
                if(this.project.body.length > this.bodyMaxLen){
                    return this.project.body.substr(0,this.bodyMaxLen) + '...';
                }
                return this.project.body;            
            }
        }
    }
</script>

<style lang="scss" scoped>

</style>