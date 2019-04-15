<template>
    <div class="score">
        Votre Score : {{ score }}
    </div>
</template>

<script>
export default {
  name: 'Score',
  data: function () {
    return { score: 0 }
  },
  created: function () {
    this.score++
  }
}
</script>

<style scoped>
</style>
