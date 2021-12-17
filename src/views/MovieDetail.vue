<template>
  <div class="movie-detail">
    <div>
      <img :src="movie.Poster" alt="movie" class="img" />
    </div>
    <div class="movie-text">
      <h1>{{ movie.Title }}</h1>
      <h5>---- {{ movie.Year }} ----</h5>

      <p>{{ movie.Plot }}</p>
    </div>
  </div>
</template>
<script>
import { ref, onBeforeMount } from "vue";
import { useRoute } from "vue-router";

export default {
  setup() {
    const movie = ref({});
    const route = useRoute();
    onBeforeMount(() => {
      fetch(
        `https://www.omdbapi.com/?&apikey=be90f806&i=${route.params.id}&plot=full`
      )
        .then((res) => res.json())
        .then((data) => {
          movie.value = data;
        });
    });
    return {
      movie,
    };
  },
};
</script>
<style>
img {
  width: 300px;
}
.movie-detail {
  display: flex;
  justify-content: space-between;
  align-items: center;

  padding: 10px;
}
h1,
h5 {
  text-align: center;
  margin: 20px 0;
}

.movie-text {
  color: white;
  padding-left: 20px;
  text-align: start;
}
</style>
