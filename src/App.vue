<template>
  <div id="app">
    <TranslateForm v-on:formSubmit="textTranslate"></TranslateForm>
    <TranslateOutput v-text="translatedText"></TranslateOutput>
  </div>
</template>

<script>
import TranslateForm from './components/TranslateForm'
import TranslateOutput from './components/TranslateOutput'
export default{
   name: 'App',
   data:function(){
     return{
       translatedText:''
     }
   },
   components:{
     TranslateForm,
     TranslateOutput
   },
   methods:{
     textTranslate: function(text,language){
       this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20191026T123447Z.4f0dcc76dfdd5f49.e6ef391fc2d715917832e03af6fc760d2eb998c6&lang='+language+'&text='+text).then((res)=>{
         this.translatedText=res.body['text'][0];
       });

     }
   }
}
</script>
//@author:sanchit-mishra
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
