<template>
    <div id="filmlist">
        <ul>
            <films-list-item v-for="(film, index) in films" :film="film" :key="index"></films-list-item>
        </ul>
    </div>
</template>

<script>
import filmsListItem from './filmsListItem.vue'

export default {
    name: 'films-list',
    props: ['films'],
    components: {
        'films-list-item': filmsListItem
    }
}
</script>

<style>

</style>