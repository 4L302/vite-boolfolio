<script>
import axios from "axios";
import MainComponent from "./components/MainComponent.vue";

export default {
  'name': "App",
  data(){
    return{
      title: 'Boolfolio',
      products: [],
      apiUrl: 'http://127.0.0.1:8000/api/'
    }
  },
  methods: {
    getData(){
      axios.get(`${this.apiUrl}/projects`).then((res) => {
        console.log(res);
      })    
    }
  },
  mounted(){
    this.data();
  }
}
</script>

<template>
  
</template>

<style scoped>

</style>
