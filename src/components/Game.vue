<template>
  <div class="game" v-on:click="clickOnInterface">
    <!-- v-on pour gerer des evennements, dans ce cas de type click et appel la fonction clickOnRound -->
    <span class="round" ref="round" v-on:click.stop="clickOnRound" v-on:click.alt.stop="bonus"></span>
  </div>
</template>

<script>
export default {
  name: 'game',
  data: function () {
    return {click: 0}
  },
  created: function () {
    document.onkeydown = this.start
  },
  // pour regarder une proprieté
  watch: {
    click: function () {
      console.log(this.click)
    }
  },
  methods: {
    clickOnRound: function (event) {
      this.click++
      this.updateRound()
    },
    bonus: function (event) {
      console.log(event)
    },
    clickOnInterface: function (event) {
      this.click++
      console.log('INTERFACE')
      console.log(this.$refs)
    },
    start: function (event) {
      if (event.key === 'Enter') {
        console.log('START')
      }
    },
    updateRound: function () {
      let element = this.$refs.round
      // Pour changer la taille de l'élément
      let size = Math.random() * (100 - 10) + 10
      element.style.height = element.style.width = `${size}px`
      // Pour changer la position de l'élément
      let top = Math.random() * (35 - 5) + 5
      let left = Math.random() * (60 - 5) + 5
      element.style.margin = `${top}% ${left}%`
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.game {
  width: 100%;
  height: 50%;
  display: block;
  background: darkslategrey;
}
.round {
  width: 50px;
  height: 50px;
  background: aliceblue;
  border-radius: 9999px;
  position: absolute;
  margin: 20% 20%;
}
</style>
