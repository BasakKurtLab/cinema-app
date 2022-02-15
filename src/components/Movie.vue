<template>
  <div class="card">
    <router-link :to="movieDetailsPath">
      <img class="card-img-top" :src="posterPath" :alt="movie.original_title">
    </router-link>
    <div class="card-block">
      <router-link :to="movieDetailsPath" style="text-decoration: none; color: inherit;">
        <h4 class="card-title">{{movie.original_title}}</h4>
      </router-link>
      <p class="card-text">{{movie.overview}}</p>
    </div>
    <div class="card-footer">
      <small class="text-muted text-right"><span>Rating:</span> {{movie.vote_average.toFixed(1)}}</small>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    movie: { type: Object, required: true }
  },
  computed: {
    posterPath() {
      return `https://image.tmdb.org/t/p/w500${this.movie.poster_path}`;
    },
    movieDetailsPath() {
      return `/movie/${this.movie.id}`;
    }
  }
}
</script>

<style scoped>
.card {
  margin-bottom: 30px;
  min-width: 200px;
  border: 1px solid #121212;
  background-color:#121212;
  color:aliceblue;
}

h4.card-title{
  color:#f5c518;
  text-decoration: none;
}
span{
  color:#f5c518;
}
.text-muted{
  font-size:16px;
  font-weight: 600;
}

.card-footer{
  background-color: #0c0c0c;
  color:rgb(238, 242, 245);
  font-weight: 600;
}
.card img {
  width: 100%;
}
</style>
