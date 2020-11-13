<template>
  <div class="ingame">
    <img alt="good-luck" class="rounded mx-auto d-block img-fluid" src="../assets/good.jpg" height="20px">
    <div class="card-deck mt-5">
    <div class="card">
    <div class="card-body">
      <h3 class="card-title text-center">Guess the song !</h3>
      <button type="button" @click="fetchSong()" class="btn btn-primary">Play Game</button>
      <source :src="song" type="audio/ogg">
      <button type="button" class="btn btn-primary">Next</button>
    </div>
  </div>
  <div class="card">
    <div class="card-body">
      <h3 class="card-title text-center">Players</h3>
    </div>
    <div class="container">
    <div class="row justify-content-center">
    <div class="col-4 text-center">
      <p>Player 1</p>
    </div>
    <div class="col-4 text-center">
     <p>Player 2</p>
    </div>
    </div>
  </div>
  </div>
</div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'ingame',
  components: {
  },
  methods: {
    fetchSong () {
      axios({
        url: 'http://localhost:3000/songs',
        methods: 'GET'
      })
        .then(({ data }) => {
          this.songs = data
          this.song = data[0].embed
          console.log(data)
        })
        .catch(err => {
          console.log(err)
        })
    }
  },
  data () {
    return {
      songs: [],
      song: ''
    }
  }
}
</script>

<style scoped>

</style>
