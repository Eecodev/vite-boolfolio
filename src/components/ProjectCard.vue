<template>
    <div>
        <router-link :to="{ name: 'single-project', params: {id: project.id} }" class="btn btn-primary">
                {{ project.title }}
        </router-link>
    </div>
</template>

<script>
    export default {
        name: 'ProjectCard',
        // props: ['project']
    }
</script>

<style lang="scss" scoped>

</style>