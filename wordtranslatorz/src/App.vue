<template>
  <div class="text-center" id="app">
  <h1>Word Translator</h1>
  <h5>Powered By Vue.js</h5>
  <TranslateForm v-on:formSubmit="translateText"></TranslateForm>
  <TranslateOutput v-text="translatedText"></TranslateOutput>
  </div>
</template>

<script>
import TranslateForm from './components/TranslateForm'
import TranslateOutput from './components/TranslateOutput'

export default {
  name: 'app',
  components: {
    TranslateForm,
    TranslateOutput
  },
  data: function() {
    return {
    translatedText:''
    }
  },
  methods: {
    translateText: function(text, language) {
      this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20170423T012216Z.045b94543a46d738.16ab97aa7dd899dbac1d0ebac09f897bfc72e828&lang='+language+'&text='+text)
      .then((response) => {
        this.translatedText = response.body.text[0];
      });
    }
  }
}
</script>
<style>
body {
  background: #fefefe;
}

</style>
