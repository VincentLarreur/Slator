<template>
  <div class="translator">
    <div class="step-init" v-if="currentStep === 0">
      <p>Drag and Drop your .json file</p>
      <p class="or">OR</p>
      <label for="file" class="slator-btn">Select file to Upload</label>
      <input id="file" class="input-file" type="file"/>
    </div>

    <div class="step-language" v-else-if="currentStep === 1">
      <div class="valid-message">
        <svg width="12px" height="9px" viewBox="0 0 12 9" version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink">
            <g id="Page-1" stroke="none" stroke-width="1" fill="none" fill-rule="evenodd">
                <g id="Valid" transform="translate(-701.000000, -342.000000)" fill="#FFFFFF">
                    <g id="Group-8" transform="translate(538.000000, 324.000000)">
                        <g id="Group-5" transform="translate(133.000000, 0.000000)">
                            <g id="Group-9" transform="translate(24.000000, 10.000000)">
                                <path d="M11.4319162,16.5895163 C10.887858,17.1368279 10.0050765,17.1368279 9.46128093,16.5895163 L6.40804359,13.5180207 C5.86398547,12.9709732 5.86398547,12.0829127 6.40804359,11.5358652 C6.95183913,10.9885537 7.83462069,10.9885537 8.3786788,11.5358652 L10.1978075,13.3656081 C10.3351349,13.5034926 10.5580622,13.5034926 10.6956522,13.3656081 L15.6213212,8.41048368 C16.1651167,7.86317211 17.0478983,7.86317211 17.5919564,8.41048368 C17.8532198,8.67330946 18,9.02990726 18,9.4015614 C18,9.77321554 17.8532198,10.1298133 17.5919564,10.3926391 L11.4319162,16.5895163 Z" id="Path"></path>
                            </g>
                        </g>
                    </g>
                </g>
            </g>
        </svg>
        <span>Valid Json file provided</span>
      </div>
      <div>
        <VueMultiselect
          label="Select your source language"
          v-model="selectedFrom"
          :options="options"
          placeholder="Select language"
          :close-on-select="true"
          :clear-on-select="false"
        />

        <VueMultiselect
          label="Select your source language"
          v-model="selectedTo"
          :options="options"
          placeholder="Select language"
          :close-on-select="true"
          :clear-on-select="false"
        />
      </div>
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
import { Options, Vue } from 'vue-class-component'

enum Step {
  Init,
  Language,
  Loading,
  Result,
  Error
}

@Options({
  components: {
  }
})
export default class Translator extends Vue {
  private currentStep = Step.Language;

  private selectedFrom = null;

  private selectedTo = null;

  private options = ['French', 'English', 'Spanish', 'Arabic'];
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

  .step-language {
    .valid-message {
      position: absolute;
      top: 30px;
      left: 50%;
      transform: translateX(-50%);
      background: #1E223E;
      border-radius: 0 0 5px 5px;
      padding: 10px;
      display: flex;
      align-content: center;
      svg {
        background-color: #83C33D;
        border-radius: 50%;
        height: 10px;
        width: 10px;
        padding: 3px;
        border: solid 2px white;
        margin-right: 5px;
      }
      span {
        font-family: Helvetica;
        font-size: 14px;
        color: #777C9D;
        letter-spacing: 0;
        padding-top: 2px;
      }
    }
  }

  .slator-btn {
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
  .slator-btn:hover {
    background: #024988;
    border: 2px solid #024988;
  }

  .input-file {
      display: none;
  }
}
</style>
