<template>
  <nav class="navbar navbar-expand-lg bg-body-tertiary">
    <div class="container-fluid">
      <a class="navbar-brand" href="#">Mahdi Nasser</a>
      <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarSupportedContent">
        <ul class="navbar-nav me-auto mb-2 mb-lg-0">

          <li class="nav-item" v-for="(item, index) in menu" :key="index">
              <router-link class="nav-link active" :to="{name: item.name}">{{item.label}}</router-link>
          </li>

        </ul>
        <form class="d-flex" role="search">
          <input class="form-control me-2" type="search" placeholder="Search" aria-label="Search">
          <button class="btn btn-outline-success" type="submit">Search</button>
        </form>
      </div>
    </div>
  </nav>
</template>

<script>
    export default {
        name: "AppHeader",
        data(){
            return {
                menu: 
                [
                    {
                      label: "Home",
                      name: "home",
                        
                    },
                    {
                      label: "Projects",
                      name: "projects",
                    },
                    {
                      label: "Contacts",
                      name: 'contacts',
                    }
                ],
            }
        }
    }
</script>

<style lang="scss" scoped>

</style>