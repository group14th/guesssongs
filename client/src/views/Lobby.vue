<template>
  <div id="lobby-page" class="container d-flex justify-content-center">
    <div class="card px-3 py-3" style="background-color: #f54242; width: 25rem; margin: 34px">
      <img src="../assets/boy.png" class="card-img-top" alt="" />
      <div class="card-body text-light">
        <h2 class="card-title">Welcome {{ username }}</h2>
        <p class="card-text">Are you ready to play?</p>
        <a href="" class="btn btn-light mr-1">YEP!!</a>
        <a href="" class="btn btn-light" @click.prevent="toLanding">Aww Not Yet</a>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Lobby',
  data () {
    return {
      username: localStorage.getItem('username')
    }
  },
  methods: {
    toLanding () {
      localStorage.clear()
      this.$router.push('/')
    }
    // toGame () {
    //   this.$router.push('/')
    // }
  }
}
</script>

<style>
</style>
