<template>
  <div class="home">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
    <div style="display: flex; flex-wrap: wrap">
      <div v-for="films in mesFilms" :key="films.name">
        <a href=""><img alt="Vue logo" :src="'https://image.tmdb.org/t/p/original' + films.backdrop_path" width="380.6"></a>
        
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'
import axios from 'axios';

export default {
  name: 'Home',
  components: {
    HelloWorld
  },
  data(){
    return{
      mesFilms : null,
    }
  },
  mounted(){
    this.getFilms();
  },
  methods:{
    getFilms(){
      axios
        .get('https://api.themoviedb.org/3/movie/popular?api_key=029a8e8d1260924d13c45ff97e1bcb8a&language=fr')
        .then((response) =>{
            this.mesFilms = response.data.results
            console.log(this.mesFilms)
        } )
        .catch(error => console.log(error))
    }
  }
}
</script>
