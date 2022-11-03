<template>
    <div  class="movie-list list-group">
        <MovieListItem v-for="movie in movies" v-bind:movie="movie" />
    </div>
</template>
<script>
import MovieListItem from '../movie-list-item/MovieListItem.vue';
export default {
    components: {
        MovieListItem,
    },
    data(){
        return{
        movies:[
            {
                name: "gumbaz ostida",
                viewers: 822,
                favorite: true,
                like: true,
            },
            {
                name: "Qasoskorlar",
                viewers: 999,
                favorite: false,
                like: false,
            },
            {
                name: "Lutsifer",
                viewers: 822,
                favorite: false,
                like: true,
            },
        ],
     }
    }
}
</script>
<style scoped>
    .movie-list{
        margin-top: 2rem;
        padding: 1.5rem;
        background-color: #fcfaf5;
        border-radius: 4px;
        box-shadow: 15px 15px 15px rgba(0, 0, 0,.15);
    }
</style>