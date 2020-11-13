<template>
  <div id="lobby-page" class="container">
    <div class="row">
      <div
        class="card px-3 py-3 col-3 my-2 text-light"
        style="background-color: #f54242; margin: 0 auto"
      >
        <img src="../assets/boy.png" class="card-img-top" alt="" />
        <h2 class="my-2">Online users</h2>
        <ul
          class="list-group list-group-flush"
          style="background-color: #f54242"
        >
          <OnlineUsers></OnlineUsers>
        </ul>
      </div>
      <div
        class="card px-3 py-3 col-7 my-2"
        style="background-color: #f54242; margin: 0 auto"
      >
        <img src="../assets/body-bg.jpg" class="card-img-top" alt="" />
        <div class="card-body text-light">
          <h2 class="card-title">Welcome, {{ username }}!</h2>
          <p class="card-text">Are you ready to play?</p>
          <a href="" class="btn btn-light mr-1">YEP!!</a>
          <a href="" class="btn btn-light" @click.prevent="toLanding"
            >Noo, I'm done</a
          >
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import swal from 'sweetalert'
import OnlineUsers from '../components/OnlineUsers'
export default {
  name: 'Lobby',
  components: {
    OnlineUsers
  },
  data () {
    return {
      username: localStorage.getItem('username')
    }
  },
  methods: {
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
          swal(
            "Oof, you have been back to the landing page. Don't forget to re-fill the username form!",
            {
              icon: 'info'
            }
          )
        } else {
          swal("You are not leaving, aren't you? Be prepared for the game!")
        }
      })
    }
    // toGame () {
    //   this.$router.push('/')
    // }
  }
}
</script>

<style>
</style>
