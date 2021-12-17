<template>
  <div class="home">
    <!-- <div class="new-movie">
      <div class="card">
        <router-link to="/movie/tt234">
          <img
            src="https://m.media-amazon.com/images/M/MV5BMTk4OTU3NzY0MV5BMl5BanBnXkFtZTcwMDU5MTgwOQ@@._V1_SX300.jpg"
            alt="spidider"
            class="image"
          />
          <div class="card-detail">
            <h3>Along Came a Spider</h3>
            <p>
              Lorem ipsum dolor sit amet consectetur adipisicing elit.
              Architecto, illum. Labore velit aliquam facilis? Accusamus,
              provident sed
            </p>
          </div>
        </router-link>
      </div>
      <div class="card">
        <router-link to="/movie/tt234">
          <img
            src="https://m.media-amazon.com/images/M/MV5BMTk4OTU3NzY0MV5BMl5BanBnXkFtZTcwMDU5MTgwOQ@@._V1_SX300.jpg"
            alt="spidider"
            class="image"
          />
          <div class="card-detail">
            <h3>Along Came a Spider</h3>
            <p>
              Lorem ipsum dolor sit amet consectetur adipisicing elit.
              Architecto, illum. Labore velit aliquam facilis? Accusamus,
              provident sed
            </p>
          </div>
        </router-link>
      </div>
      <div class="card">
        <router-link to="/movie/tt234">
          <img
            src="https://m.media-amazon.com/images/M/MV5BMTk4OTU3NzY0MV5BMl5BanBnXkFtZTcwMDU5MTgwOQ@@._V1_SX300.jpg"
            alt="spidider"
            class="image"
          />
          <div class="card-detail">
            <h3>Along Came a Spider</h3>
            <p>
              Lorem ipsum dolor sit amet consectetur adipisicing elit.
              Architecto, illum. Labore velit aliquam facilis? Accusamus,
              provident sed
            </p>
          </div>
        </router-link>
      </div>
      <div class="card">
        <router-link to="/movie/tt234">
          <img
            src="https://m.media-amazon.com/images/M/MV5BMTk4OTU3NzY0MV5BMl5BanBnXkFtZTcwMDU5MTgwOQ@@._V1_SX300.jpg"
            alt="spidider"
            class="image"
          />
          <div class="card-detail">
            <h3>Along Came a Spider</h3>
            <p>
              Lorem ipsum dolor sit amet consectetur adipisicing elit.
              Architecto, illum. Labore velit aliquam facilis? Accusamus,
              provident sed
            </p>
          </div>
        </router-link>
      </div>
    </div> -->
    <form @submit.prevent="SearchMovies()" class="search-form">
      <input type="text" placeholder="Searc Movie" v-model="search" />
      <input type="submit" value="Search" />
    </form>
    <div class="movies">
      <div class="movie" v-for="movie in movies" :key="movie.imdbID">
        <router-link :to="'/movie/' + movie.imdbID">
          <div class="type">
            <h4>{{ movie.Type }}</h4>
          </div>
          <img :src="movie.Poster" :alt="movie.imdbID" class="movie-img" />

          <div class="movie-info">
            <h3>{{ movie.Title }}-{{ movie.Year }}</h3>
          </div>
        </router-link>
      </div>
    </div>
  </div>
</template>

<script>
import { ref } from "vue";
export default {
  setup() {
    const search = ref("");
    const movies = ref([]);

    const SearchMovies = () => {
      if (search.value != "") {
        fetch(
          `https://www.omdbapi.com/?s=${search.value}&page=2&apikey=be90f806`
        )
          .then((res) => res.json())
          .then((data) => {
            movies.value = data.Search;
            search.value = "";
            console.log(movies.value);
          });
      }
    };
    return {
      search,
      movies,
      SearchMovies,
    };
  },
};
</script>

<style>
.card {
  position: relative;
  width: 100%;
}
.new-movie {
  display: flex;
  padding-top: 30px;
  justify-content: space-around;
}
.card {
  width: 300px;
}
.image {
  display: block;
  position: relative;
  z-index: 0;
}

.card-detail {
  position: absolute;
  left: 0;
  bottom: 0;
  right: 0px;
  background-color: rgba(57, 62, 70, 0.85);
  z-index: 1;
  padding: 12px;
}
h3 {
  color: #00adb5;
}
p {
  padding-top: 10px;
  color: #eeeeee;
}
.search-form {
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
}
input {
  display: block;
  appearance: none;
  border: none;
  outline: none;
  background: none;
}
[type="text"] {
  width: 50%;
  color: white;
  background-color: #393e46;
  font-size: 20px;
  padding: 10px 15px;
  border-radius: 8px;
  margin: 18px;
  transition: 0.4s;
}
[type="text"]::placeholder {
  color: white;
}
[type="text"]:focus {
  background-color: rgba(57, 62, 70, 0.36);
  width: 55%;
}
[type="submit"] {
  display: block;
  color: white;
  background-color: #00adb5;
  width: 30%;
  height: 70px;
  border-radius: 8px;
  font-size: 30px;
  font-weight: bold;
}
.movies {
  display: flex;
  flex-wrap: wrap;

  justify-content: space-between;
}
.movie {
  width: 300px;
  margin: 10px;
}
.movie-img {
  display: flex;
  width: 100%;
  height: 400px;
}
.movie-info {
  background-color: rgba(57, 62, 70, 0.85);
  height: 50px;
}
.type {
  position: absolute;
  background-color: rgba(57, 62, 70, 0.85);
  z-index: 3;
  padding: 15px;
  width: 100px;
  text-align: center;
  margin-top: 90px;
}
</style>
