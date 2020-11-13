<template>
  <div class="ingame">
    <img alt="good-luck" class="rounded mx-auto d-block img-fluid" src="../assets/good.jpg" height="20px">
    <div class="card-deck mt-5">
    <div class="card">
    <div class="card-body">
      <h3 class="card-title text-center">Guess the song !</h3>
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

export default {
  name: 'ingame'
}
</script>

<style scoped>

</style>
