<template>
  <div class="container">
    <h1 class="text-center">My Projects</h1>
    <div v-if="projects" class="projs p-4 d-flex gap-3 flex-wrap ">
      <div class="card singleProj" v-for="proj in projects" style="width: 18rem;">
        <div class="card-body">
          <h5 class="card-title">{{ proj.title }}</h5>
          <p class="card-text">{{ proj.description }}</p>   
          <RouterLink class="btn btn-primary" :to="{name:'project', params: { slug: proj.slug }}">More Details</RouterLink>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { store } from '../store/store';
import axios from 'axios';
export default {
  name: 'HomeView',
  data() {
    return {
      store,
      projects: false,

    }
  },
  methods: {
    getProjs() {
      axios.get(store.apiUrl).then(res => {
        this.projects = res.data.results.data;
        console.log(this.projects);
      });
    }
  },
  components: {

  },
  mounted() {
    this.getProjs()
  }
}
</script>

<style lang="scss" scoped></style>