<template>
    <div v-if="film" id="detail">
        <h2>{{film.title}}</h2>
        <p>Description: {{film.description}}</p>
        <p>Director: {{film.director}}</p>
        <p>Producer: {{film.producer}}</p>
        <p>Year Released: {{film.release_date}}</p>
        <p>Rotton Tomatoes Score: {{film.rt_score}}</p>

        <button v-on:click="addToWatchList">Add to Watch List</button>
    </div>
</template>

<script>
import { eventBus } from '@/main.js'


export default {
    name: 'film-details',
    props: ['film', 'selected-film', 'watchList'],
    methods: {
        addToWatchList: function(){
            eventBus.$emit('add-film', this.film)
        }
    }
}
</script>

<style>

#detail {
    animation: fade 1.5s ease forwards;
}

@keyframes fade {
    from{
        opacity: 0;
    }
    to{
        opacity: 1;
    }
}

</style>