<template>
    <div>
      <!-- v-hide est une directive personnalisee -->
      <!-- v-html permet d'injecter du html à l'interieur -->
      <span v-html="welcomeMsg" v-hide></span>
      <!-- prevent detruit le fonctionnement classique de submit et ne va plus recharger la page-->
      <form v-hide v-on:submit.prevent="setPlayer">
        <input name="player" placeholder="Entrez votre nom de joueur" v-border:red/>
        <button type="submit">Jouer</button>
      </form>
    </div>
</template>

<script>
export default {
  name: 'player',
  data: function () {
    // pour rendre une variable reactive, il faut la metre en data
    return {
      player: '',
      welcomeMsg: ''
    }
  },
  updated: function () {
    this.welcomeMsg = `Bonjour <span>${this.player} </span>!`
  },
  methods: {
    setPlayer: function (event) {
      // console.log(event)
      let playerName = event.target[0].value
      // si le nom n'est pas indiqué, je montre une alerte
      if (!playerName) {
        alert('Merci de renseigner votre pseudo')
        return
      }
      this.player = playerName
      // console.log(this.player)
    }
  },
  directives: {
    border: function (el, binding) {
      el.style.borderColor = binding.arg
    },
    // directive v-hide
    hide: function (el, binding, vnode) {
      // console.log(binding)
      // console.log(vnode)
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
