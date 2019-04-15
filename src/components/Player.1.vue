<template>
    <div>
      <!-- v-hide est une directive personnalisee -->
      <span v-hide>{{welcomeMsg}}</span>
      <form v-hide>
        <input name="player" placeholder="Entrez votre nom de joueur" v-border:red/>
        <button type="submit">Envoyer</button>
      </form>
    </div>
</template>

<script>
export default {
  name: 'Player',
  created: function () {
    this.player = 'Cindy'
    this.welcomeMsg = this.player ? 'Bonjour ' + this.player + ' !' : 'Pas de joueur'
  },
  directives: {
    border: function (el, binding) {
      el.style.borderColor = binding.arg
    },
    // directive v-hide
    hide: function (el, binding, vnode) {
      console.log(vnode)
      // Je verifie si c'est un form ou pas
      let isForm = vnode.tag === 'form'
      // Je recupere le player - vide s'il y en a pas
      let player = vnode.context.player

      if (isForm) {
        // si c'est un form
        // s'il y a un joueur, on cache le form
        el.style.display = player ? 'none' : 'block'
      } else {
        // si c'est un span et il y a un joueur, on montre le span
        el.style.display = player ? 'block' : 'none'
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
