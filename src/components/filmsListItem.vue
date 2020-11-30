<template>
    <div>
        <li v-on:click="handleClick">{{film.title}}</li>
    </div>
</template>

<script>
import {eventBus} from '../main.js';

export default {
    name: 'films-list-item',
    props: ['film'],
    methods: {
        handleClick(){
            eventBus.$emit('selected-film', this.film)
        }
    }
}
</script>

<style>

</style>