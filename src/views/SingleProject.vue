<template>
    <div class="container">
        <div class="wrap">
            <table class="table">
                <thead>
                    <tr class="fs-3">
                        <th scope="col">Title</th>
                        <th scope="col">Description</th>
                        <th scope="col">Type</th>
                        <th scope="col">Technologies</th>
                    </tr>
                </thead>
                <tbody class="fs-4">
                    <tr v-if="project">
                        <th scope="row">{{ project.title }}</th>
                        <td id="description">{{ project.description }}</td>
                        <td>{{ project.type.name }}</td>
                        <td v-if="project.technologies.length > 0">
                            <span class="rounded-pill bg-warning py-2 px-3 m-2" v-for="tech in project.technologies">{{ tech.name }}</span>
                        </td>
                        <td v-else>No Techs</td>
                    </tr>
                </tbody>
            </table>
        </div>
    </div>
</template>
  
<script>
import { store } from '../store/store';
import axios from 'axios'
export default {
    name: 'SingleProject',
    data() {
        return {
            project: null
        }
    },
    methods: {
        getProj() {
      axios.get(store.apiUrl + this.$route.params.slug).then(res => {
        this.project = res.data.result;
        console.log(this.project);
      });
    }
    },
    components: {

    },
    mounted() {
        this.getProj();
    }
}
</script>
  
<style lang="scss" scoped>
#description{
    width: 30% ;
}

</style>