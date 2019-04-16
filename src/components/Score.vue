<template>
    <div class="score">
        {{ score ? 'VOTRE SCORE : ' + score : 'Appuyez sur entrée pour démarrer' }}
    </div>
</template>

<script>
export default {
  name: 'score',
  data: function () {
    return { score: 0 }
  }
}
</script>

<style scoped>
</style>
