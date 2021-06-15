<template>
  <div class="about" style="background-color: #A9957B">
    <h1>Page ma liste</h1>
     
    <HelloWorld msg="Welcome to Your Vue.js App"/>
    
    <div v-for="films in mesFilms" :key="films.name" style="border : 1px solid black; display: flex; justify-content: space-around;align-items: center; padding: 10px 10px 10px 10px; background-color: #F5F5DC; flex-wrap: wrap">
        
        <img alt="Vue logo" :src="'https://image.tmdb.org/t/p/original' + films.backdrop_path" height="300">
        <div style="display: flex; flex-direction: column; justify-content: center; width: 500px; min-width: 300px; padding: 10px 10px 10px 10px">
          <h1 style="color: orangered">Titre : {{films.original_title}}</h1>
          <p><strong>Film Adult booleen : </strong>{{films.adult}}</p>
          <p><strong>Genre du film : </strong>{{films.genre_ids}}</p>
          <p><strong>Langue original du film : </strong>{{films.original_language}}</p>
          
          <p><strong>Vote  : </strong>{{films.vote_average}}/10</p>
          <p><strong>Nombre de Vote : </strong>{{films.vote_count}}</p>
          <p><strong>Résumé : </strong>{{films.overview}}</p>
          
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
    this.getVaisseaux();
  },
  methods:{
    getVaisseaux(){
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