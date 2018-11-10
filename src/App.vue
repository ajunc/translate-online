<template>
  <div id="app">
    <h1>在线翻译</h1>
    <h5 class="text-muted">简单 / 易用 / 便捷</h5>
    <translateForm v-on:formSubmit="translateText"></translateForm>
    <translateOutput v-text="translatedText"></translateOutput>
  </div>
</template>

<script>
import TranslateForm from './components/TranslateForm'
import translateOutput from './components/translateOutput'
export default {
  name: 'App',
  data: function() {
    return{
      translatedText:''
    }
  },
  components: {
    TranslateForm,
    translateOutput
  },
  methods:{
    translateText:function(text,language){
      //alert(text);
      this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20181110T123846Z.c2b82bf22ee2fcef.4eb0f9dd501a10ae518ad2df948a19eb5e3e9955&lang='+language+'&text='+text)
      .then((response)=>{
        //console.log(response.body.text[0]);
        this.translatedText = response.body.text[0];
      })
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
