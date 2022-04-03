<template>
  <div>
      <div v-for="(sentence, index) in sentences" 
        :key="index" 
        :class="{ active: index === currentSentenceProps}" class="m-5 p-2 rounded-pill border border-secondary sceneContainer">
          {{ sentence.txt }}
      </div>
  </div>
</template>

<script>
export default {
    name: 'EscenaComponent',
    props: ['sentences', 'currentSentenceProps']
}
</script>

<style scoped>   
    .sceneContainer{
        background-color: rgba(255,255,255,0.9);
        font-size: 1.2rem;
    }
    .active{
        background-color: rgba(3, 252, 202,0.9);
    }
</style>