<template>
    <div class="movie-add-form">
      <h3> yangi kino qo'shish</h3> 
      <form class="add-form d-flex" @submit.prevent>
        <input type="text" 
        class="form-control new-movie-label" 
        :value="name" 
        placeholder="Qanday kino?"
        @input="name = $event.target.value"
        />
        <input
        type="number" 
        class="form-control new-movie-label" 
        placeholder="Nechi marotaba ko'rilgan?"
        :value="viewers"
        @input="viewers = $event.target.value"
        />
        <button class="btn btn-outline-dark" @click="addMovie" type="submit">qo'shish</button>
      </form>
    </div>
</template>
<script>
export default {
    data(){
      return{ 
        name: '',
        viewers: '',
      }
    },
    methods:{
      addMovie(){
        const newMovie = {
          id: Date.now(),
          name: this.name,
          viewers: this.viewers,
          favorite: false,
          like: false,
        }
        this.$emit('createMovie',newMovie)
        this.name=''
        this.viewers=''
      },
    },
}
</script>
<style>
    .movie-add-form{
      margin-top: 2rem;
      padding: 1.5rem;
      background-color: #fcfaf5;
      border-radius: 4px;
      box-shadow: 15px 15px 15px rgba(0, 0, 0,.15);
    }
</style>