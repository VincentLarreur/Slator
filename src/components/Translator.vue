<template>
  <div class="translator">
    <div class="step-init" v-if="currentStep === 0">
      <p>Drag and Drop your .json file</p>
      <p class="or">OR</p>
      <label for="file" class="label-file">Select file to Upload</label>
      <input id="file" class="input-file" type="file"/>
    </div>
    <div class="step-language" v-else-if="currentStep === 1">
      language
    </div>
    <div class="step-loading" v-else-if="currentStep === 2">
      loading
    </div>
    <div class="step-result" v-else-if="currentStep === 3">
      result
    </div>
    <div class="step-error" v-else>
      error
    </div>
  </div>
</template>

<script lang="ts">
import { Vue } from 'vue-class-component'

enum Step {
  Init,
  Language,
  Loading,
  Result,
  Error
}

export default class Translator extends Vue {
  private currentStep = Step.Init;
}
</script>

<style scoped lang="scss">
.translator {
  width: 100%;
  height: 90%;
  display: flex;
  justify-content: center;
  align-items: center;
  .step-init {
    width: 60%;
    height: 50%;
    border: dashed 2px #0E1022;
    border-radius: 10px;
    display: flex;
    justify-content: space-evenly;
    align-items: center;
    flex-direction: column;
    padding: 30px;
    p {
      margin: 0;
      font-size: 14px;
      font-family: Helvetica;
      color: #84879E;
      letter-spacing: 0;
      &.or {
        color: #4D516F;
      }
    }
  }

  .label-file {
    cursor: pointer;
    width: 50%;
    min-width: 200px;
    height: 50px;
    background: #0087FF;
    border: 2px solid #0087FF;
    border-radius: 3px;
    font-family: Helvetica;
    line-height: 50px;
    font-size: 16px;
    color: #FFFFFF;
    letter-spacing: 0;
    text-align: center;
  }
  .label-file:hover {
    background: #024988;
    border: 2px solid #024988;
  }

  .input-file {
      display: none;
  }
}
</style>
