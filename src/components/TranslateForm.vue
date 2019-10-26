<template>
  <div id="translateForm">
    <form v-on:submit="submitForm">
     <input type="text" v-model="textToTranslate" placeholder="Input your content here:"/>
      <select v-model="language">
          <option value="en">English</option>
          <option value="hi">Hindi</option>
          <option value="fr">French</option>
          <option value="mr">Marathi</option>
      </select>
      <input type="submit" value ="Translate" />
    </form>
  </div>
</template>

<script>
export default {
  name: 'TranslateForm',
  data: function(){
    return {
      textToTranslate:"",
      language:'en'
    }
  },
  methods: {
    submitForm:function(e){
    //  alert(this.textToTranslate);
      this.$emit("formSubmit", this.textToTranslate,this.language);
      e.preventDefault();
    }
  }
}
</script>
