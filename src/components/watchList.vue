<template>
    <div v-if="film">
        <h3>Watch List</h3>
        <ul>
            <li v-for="(film, index) in watchList" :key="index">{{film.title}}</li>
        </ul>
    </div>
</template>

<script>
export default {
    name: 'watch-list',
    props: ['film', 'watchList']
}
</script>

<style>

li {
    list-style: none;
}

h3 {
    position: relative;
}

</style>