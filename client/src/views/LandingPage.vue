<template>
  <div id="landing-page" class="container d-flex justify-content-center">
    <div class="card my-4" style="background-color: #f54242">
      <img
        src="../assets/lp-banner.jpg"
        alt="Welcome Pic"
        style="width: 100%; height: 360px; object-fit: cover"
      />
      <div class="card-body text-light">
        <h5 class="card-title">Welcome to GUESS THAT SONG game!</h5>
        <form>
        <div class="form-group">
          <label for="username">Username</label>
          <input v-model="username" type="text" class="form-control" id="username" required/>
          <small id="emailHelp" class="form-text text-white-50"
            >This will be used as your in-game nickname.</small
          >
        </div>
        <button type="submit" class="btn btn-light" @click.prevent="letsGo">LET'S GO!</button>
      </form>
      </div>
    </div>
  </div>
</template>

<script>
import swal from 'sweetalert'
export default {
  name: 'LandingPage',
  data () {
    return {
      username: ''
    }
  },
  methods: {
    letsGo () {
      if (this.username) {
        console.log('A')
        localStorage.setItem('username', this.username)
        this.$socket.emit('letsGo', this.username)
      } else {
        swal('You forget something!', 'Username cannot be empty! Please enter anything to get into the lobby', 'info')
      }
    }
  },
  sockets: {
    'jumpto-lobby': function () {
      this.$router.push('/lobby')
      swal(`Welcome, ${this.username}!`, 'You are in game lobby! Wait for the other players', 'success')
    }
  }
}
</script>

<style>
</style>
