<template>
  <form @submit.prevent="GetDataFrom" class="well">
    <textarea style="font-weight:bold;font-size:30" v-model="txtName" class="form-control" cols=30 rows=5 placeholder="Cümle gir" />
    <select class="form-control" v-model="selectedLang">
      <option v-for="(data,key) in languages" :key="key" :value="key" >{{ data }} </option>
    </select>
    <br>
    
    <div class="text-left">
      <strong>Tespit edilen dil : </strong>{{languages[selectedLang]}}
      </div>
      <br>

       <div class="text-left" >
      <strong style="font-weight:bold;font-size:18">{{TranslationResult}}</strong>
      </div>
      <br>
      
     <button type="submit" class="btn btn-primary btn-block" > {{msg}} </button>
  </form>
    

</template>

<script>

import httpRequest from "axios"

export default {
  name: 'ButtonTest',
  data () {
      return {
      msg : "Get The Message",
      txtName : "2342421",
      languages : {},
      selectedLang : "",
      TranslationResult:""

      }
      
    
  },
  methods:{
    GetDataFrom()
    {

      if(this.selectedLang != "")
      {
         

        let translationUrl = "https://translate.yandex.net/api/v1.5/tr.json/translate?" + 
        "key=trnsl.1.1.20190620T100408Z.1d7aee4460c4cd4c.2d4995b368597cb38923d06cb3a9f6cbc671d7a7&" + 
        "text=" + this.txtName + "&lang=" + this.selectedLang

        httpRequest.get(translationUrl).then(response => 
          {
            this.TranslationResult = response.data.text[0]
            this.$emit("BroadCasting",this.TranslationResult)
          }
        ).catch(err => console.log(err))
      }
    }
    },
    created () {

       let languageUrl = "https://translate.yandex.net/api/v1.5/tr.json/getLangs?" +
      "key=trnsl.1.1.20190620T100408Z.1d7aee4460c4cd4c.2d4995b368597cb38923d06cb3a9f6cbc671d7a7&ui=tr"

        httpRequest.get(languageUrl).then(response => 
        {
          this.languages = response.data.langs
        }
      ).catch(err => console.log(err))
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->

<!--<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
button{
  width:150px;
  height:28px;
  background-color: brown;
}
textarea{
  width:200px;
  background-color: chartreuse;
  height:30px;

}
</style>-->
