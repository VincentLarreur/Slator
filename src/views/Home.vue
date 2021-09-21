<template>
  <div class="home">
    <div class="window-bar">
      <i/>
      <i/>
      <i/>
    </div>
    <translator/>
  </div>
</template>

<script lang="ts">
import { Options, Vue } from 'vue-class-component'
import Translator from '@/components/Translator.vue' // @ is an alias to /src

@Options({
  components: {
    Translator
  }
})
export default class Home extends Vue {}
</script>

<style lang="scss">
.home {
  background-color: #191C37;
  width: 40%;
  max-width: 800px;
  height: 60vh;
  max-height: 648px;
  border-radius: 5px;
  position: relative;
}

.window-bar {
  position: absolute;
  top: 0;
  right: 0;
  width: 100%;
  height: 30px;
  background-color: #111326;
  position: relative;
  border-top-left-radius: 5px;
  border-top-right-radius: 5px;
  i {
    background-color: #151933;
    width: 10px;
    height: 10px;
    border-radius: 50%;
    position: absolute;
    top: 10px;
    bottom: 10px;
    right: 10px;
    &:nth-child(1) {
      right: 30px;
    }
    &:nth-child(2) {
      right: 50px;
    }
  }
}
</style>
