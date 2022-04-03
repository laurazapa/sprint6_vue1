<template>
  <div>
    <div v-if="showWelcomePage" class="container text-center p-5 bg-dark mt-5 rounded">
      <h1 class="mb-5">Welcome!</h1>
      <p class="text-white">Lorem ipsum dolor sit amet, consectetur adipisicing elit. Ut eveniet provident harum mollitia fugiat obcaecati impedit fugit, sequi dolorem aliquam dolorum illo placeat perspiciatis! Illum dignissimos mollitia beatae eaque porro.</p>
      <button @click="startTutorial()" class="rounded-pill m-3 p-1 px-3 bg-info">Start</button>
    </div>
    <div v-else class=" text-center p-5">
        <h1>Tutorial</h1>
        <ButtonComponent :direction="'Anterior'" @currentSentenceChangeButton="currentSentenceChange(currentSentence-1)"/>
        <ButtonComponent :direction="'Seguent'" @currentSentenceChangeButton="currentSentenceChange(currentSentence+1)"/>
        <EscenaComponent :sentences="story" :currentSentenceProps="currentSentence"/>
    </div>
    <img v-if="!showWelcomePage" :src="story[currentSentence].img" :alt="story[currentSentence].txt" class="img_background">
  </div>
  
</template>

<script>
import EscenaComponent from '@/components/EscenaComponent.vue'
import ButtonComponent from '@/components/ButtonComponent.vue'
import story from '@/assets/story.js'

export default {
  name: 'HomeComponent',
  components: {
    EscenaComponent,
    ButtonComponent
  },
  data(){
    return {
      story: story,
      currentSentence: 0,
      showWelcomePage: true
    }
  },
  methods:{
    currentSentenceChange(newCurrentSentence){
      if(newCurrentSentence >= 0 && newCurrentSentence <= this.story.length-1) this.currentSentence = newCurrentSentence;
    },
    startTutorial(){
      this.showWelcomePage = false;
    }
  }

}

</script>

<style scoped>
  .img_background{
      position: absolute;
      z-index: -1;
      width: 100%;
      height: auto;
      top: 0px;
      left: 0px;
  }
  h1{
    font-size: 4rem;
    color: white;
    text-shadow: 2px 2px 5px #333;
  }
</style>