<template>
    <div class="player">{{welcomeMsg}}</div>
</template>

<script>
export default {
  name: 'Player',
  created: function () {
    this.player = 'Cindy'
    this.welcomeMsg = this.player ? 'Bonjour ' + this.player + ' !' : 'Pas de joueur'
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
