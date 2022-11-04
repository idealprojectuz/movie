<template>
<div class="app font-monospace">
  <div class="content">
      <AppInfo 
      :allMoviesCount="movies.length" 
      :favoriteMoviesCount='movies.filter(c => c.favorite).length' 
      />
  <div class="search-panel">
    <SearchPanel/>
    <AppFilter/>
  </div>
    <MovieList 
    :movies="movies" 
    @onLike="onLikeHandler" 
    @onFavorite="onFavoriteHandler"

    />
    <MovieAddForm @createMovie="createMovie" />
  </div>

</div>
</template>
<script>
import AppInfo from '@/components/app-info/Appinfo.vue';
import SearchPanel from '../search-panel/SearchPanel.vue';
import AppFilter from "../app-filter/AppFilter.vue";
import MovieList from "../movie-list/MovieList.vue";
import MovieAddForm from "../movie-add-form/MovieAddForm.vue";
  export default{
    components: {
      AppInfo,
      SearchPanel,
      AppFilter,
      MovieList,
      MovieAddForm,
    },
    data(){
        return{
        movies:[
            {
                id: 1,
                name: "gumbaz ostida",
                viewers: 822,
                favorite: true,
                like: true,
            },
            {
                id: 2,
                name: "Qasoskorlar",
                viewers: 999,
                favorite: false,
                like: false,
            },
            {
                id: 3,
                name: "Lutsifer",
                viewers: 822,
                favorite: false,
                like: true,
            },
        ],
     }
    },
    methods:{
      createMovie(item){
        this.movies.push(item)
        console.log(item)
      },
      onFavoriteHandler(id){
        this.movies=this.movies.map(item => {
          if(item.id==id) {
              item.favorite=!item.favorite
          }
          return item
        })
      }
      onLikeHandler(id) {
        this.movies=this.movies.map(item => {
          if(item.id==id) {
              item.like=!item.like
          }
          return item
        })
      },
    },
  }
</script>
<style>
.app{
  height: 100vh;
  color: black;
}
.content{
  width: 1000px;
  min-height: 700px;
  background-color: #fff;
  margin: 0 auto;
  padding: 5rem 0;
}
.search-panel{
  margin-top: 2rem;
  padding: 1.5rem;
  background-color: #fcfaf5;
  border-radius: 4px;
  box-shadow: 15px 15px 15px rgba(0, 0, 0,.15);
}
</style>