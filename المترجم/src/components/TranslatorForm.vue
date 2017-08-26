<template>
  <div class="translatorForm">
    <form id="translatorForm" @submit="formSubmit">
      <div class="field input-text">
        <label class="label">Text</label>
        <div class="control">
          <input class="input" @keyup="formSubmit" type="text" v-model="textToTranslate" placeholder="Text input">
        </div>
      </div>

      <div class="field">
        <label class="label">Language</label>
        <div class="control">
          <div class="select">
            <select @change="formSubmit" v-model="language">
              <option value="ar">Arabic</option>
              <option value="en">English</option>
              <option value="fr">French</option>
              <option value="zh">Chinese</option>
              <option value="nl">Dutch</option>
              <option value="el">Greek</option>
              <option value="it">Italian</option>
              <option value="ru">Russian</option>
            </select>
          </div>
        </div>
      </div>

    </form>
  </div>
</template>

<script>
  export default {
    name: 'translatorForm',
    data () {
      return {
        textToTranslate: '',
        language: 'ar'
      }
    },
    methods: {
      formSubmit: function(e) {
        this.$emit('formSubmit', this.textToTranslate, this.language)
        e.preventDefault()
      }
    }
  }
</script>

<style scoped>
  #translatorForm {
    display: flex;
    align-items:flex-end;
    justify-content: center;
    flex-wrap: wrap;
    padding: 50px 20px;
    width: 60%;
    border: 10px solid #00C4A7;
    outline: 2px solid #00C4A7;
    outline-offset: -15px;
  }
  .input-text{
    width: 400px;
    display: inline-block;

  }
  .field {
    margin: 10px;
    text-align: left;
  }
  .label {
    color: white
  }

</style>
