<template>
  <div>
     <!-- header form bootstrap -->
    <div>
  <b-navbar type="dark" variant="dark">
    <b-navbar-nav>
       <b-navbar-brand href="/">Movie</b-navbar-brand>
        <b-navbar-nav>
        <b-nav-item href="/toprated">Top Rated</b-nav-item>
        <b-nav-item href="/upcoming">Upcoming</b-nav-item>
      </b-navbar-nav>
    </b-navbar-nav>
  </b-navbar>
</div>
<h2 style="text-align:center; color:white ; margin:10px;">Top Rated Movies</h2>
  <TopratedMovie />
  <h2  style="text-align:center; color:white ; margin:10px;">Upcoming Movies</h2>
  <UpcomingMovie />
  </div>
</template>
<style scoped>

</style>
<script>
import TopratedMovie from "./TopratedMovie";
import UpcomingMovie from "./UpcomingMovie";

export default {
  components: {
    TopratedMovie,
    UpcomingMovie,
  },
};
</script>
