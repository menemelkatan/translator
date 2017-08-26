<template>
  <div id="app" align="center">
    <h1 class="title">Word translator</h1>
    <h2 class="subtitle">Powered by vue2.js</h2>
    <img style="display: block; height: 40px; margin-bottom: 25px" src="http://men3m.me/assets/img/my_logo.png" alt="logo">
    <TranslatorForm @formSubmit="translateText"></TranslatorForm>
    <TranslatorOutput v-text="translatedText"></TranslatorOutput>
  </div>
</template>



<script>
import TranslatorForm from './components/TranslatorForm'
import TranslatorOutput from './components/TranslatorOutput'

export default {
  name: 'app',
  components: {
    TranslatorForm,
    TranslatorOutput
  },
  data () {
    return {
      translatedText: ''
    }
  },
  methods: {
    translateText: function (text, language) {
      this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20170803T141117Z.5345d94cff4ccde1.222ea67d610b893f349faa779b9ea3732a85cd8a&lang='+language+'&text='+text).then((response) => {
          this.translatedText = response.body.text[0]
        })
    }
  }
}
</script>

<style>
  h1 {
    margin: 20px
  }
  .title, .subtitle {
    color: white
  }
</style>
