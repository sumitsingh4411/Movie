<template>
    <div>
    <div class="sty" v-for="item in movie_url" :key="item">
      <img :src="item.url" />
      <p>{{item.name}}</p>
    </div>
    </div>
</template>
<style scoped>
.sty {
  background-color: black;
  display: inline-block;
}
.sty > img {
  height: 32vh;
  width:32vw;
  margin: 0.8vh;
  object-fit:cover ;
  border:1px solid white;
  border-radius: 1vh;
  box-shadow: 0 8px 6px -6px black;
}
.sty >p{
  text-align: center;
  color:white;
}
</style>
<script>
import Vue from "vue";
import axios from "axios";
import VueAxios from "vue-axios";
Vue.use(VueAxios, axios);
// const API_KEY='7208b6d3db1406761f04e267137fca46'
export default {
  components: {},
  data() {
    return {
      movie: [],
      movie_url: [{}],
      base_url: "https://image.tmdb.org/t/p/original",
    };
  },
  mounted() {
    Vue.axios
      .get(
        "https://api.themoviedb.org/3/trending/all/week?api_key=7208b6d3db1406761f04e267137fca46&language=en-US"
      )
      .then((response) => {
        console.log(response.page);
        const data = response.data.results;
        data.map((e) => {
          const name=e.title ? e.title : e.original_name;
          const p = e.backdrop_path ? e.backdrop_path : e.poster_path;
          if(name && p)
          this.movie_url.push({url:this.base_url + p, name:name});
        });
        this.movie_url.shift();
      });
  },
};
</script>
