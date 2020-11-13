<template>
  <div id="lobby-page" class="container d-flex justify-content-center">
    <div
      class="card px-3 py-3"
      style="background-color: #f54242; width: 25rem; margin: 34px"
    >
      <img src="../assets/boy.png" class="card-img-top" alt="" />
      <div class="card-body text-light">
        <h2 class="card-title">Welcome, {{ username }}!</h2>
        <p class="card-text">Are you ready to play?</p>
        <a href="" @click.prevent="inGame()" class="btn btn-light mr-1">YEP!!</a>
        <a href="" class="btn btn-light" @click.prevent="toLanding"
          >Noo, I'm done</a
        >
      </div>
    </div>
  </div>
</template>

<script>
import swal from 'sweetalert'
export default {
  name: 'Lobby',
  data () {
    return {
      onlineUsers: [],
      username: localStorage.getItem('username')
    }
  },
  methods: {
    inGame () {
      this.$router.push('/ingame')
      console.log('this.inGame')
    },
    toLanding () {
      swal({
        title: 'Are you sure?',
        text: 'You are going to leave the lobby',
        icon: 'warning',
        buttons: true,
        dangerMode: true
      }).then((leaveLobby) => {
        if (leaveLobby) {
          localStorage.clear()
          this.$router.push('/')
          swal("Oof, you have been back to the landing page. Don't forget to re-fill the username form!", {
            icon: 'info'
          })
        } else {
          swal("You are not leaving, aren't you? Be prepared for the game!")
        }
      })
    }
    // toGame () {
    //   this.$router.push('/')
    // }
  },
  sockets: {
    'update-onlineUsers': function (onlineUsers) {
      this.onlineUsers = onlineUsers
    }
    // 'update-room': function (rooms) {
    //   this.rooms = rooms
    // }
  },
  created () {
    this.$socket.emit('get-onlineUsers')
    // this.$socket.emit('get-rooms')
  }
}
</script>

<style>
</style>
