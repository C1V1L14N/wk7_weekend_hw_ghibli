<template>
  <div id="main-view">

    <img id="main-logo" src="../src/assets/Studio_Ghibli_wordmark.svg.png" alt="Ghibli">

    <h1>Studio Ghibli Movies</h1> 
    <label for="select-film">Select Movie:</label>
    <select v-model="selectedFilm" id="select-film" >
      <option value="" disabled>Select Movie</option>
      <option :value="film" v-for="(film, index) in films" :key="index">{{film.title}}</option>
    </select>

    <!-- <div>
      <films-list :films="films"></films-list>
    </div> NO LONGER NEEDED -->

    <div id="detail-display">
      <film-details :selectedFilm="selectedFilm" :film="selectedFilm"></film-details>
    </div>
    <div id="watch-list-display">
      <watch-list :watchList="watchList" :selectedFilm="selectedFilm" :film="selectedFilm"></watch-list>
    </div>

  </div>
</template>

<script>
import filmsList from './components/filmsList.vue'
import filmDetails from './components/filmDetails.vue' 
import filmsListItem from './components/filmsListItem'
import watchList from './components/watchList.vue'

import {eventBus} from './main.js'


export default {
  name: 'app',
  data(){
    return {
      films: [],
      characters: [],
      selectedFilm: null,
      watchList: []
    }
  },
  components: {
    'films-list': filmsList,
    'film-details': filmDetails,
    'watch-list': watchList
  },
  mounted() {
    fetch('https://ghibliapi.herokuapp.com/films')
    .then(response => response.json())
    .then(data => this.films = data)

    // fetch('https://ghibliapi.herokuapp.com/people')
    // .then(response => response.json())
    // .then(data => this.characters = data)

    

    eventBus.$on('selected-film', (film) => {
      this.selectedFilm = film;
    })
    eventBus.$on('add-film', (film) => {
      this.watchList.push(film)
    })
  }

}
</script>

<style>

#main-view {
  display: flex;
  flex-direction: column;
  align-items: center;
}

select {
  width: 200px;
  height: 30px;
}

#main-logo {
  width: 500px;
  height: auto;
}





</style>