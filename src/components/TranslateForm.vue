<template>
  <div class="row" id="translate">
    <div class="col-md-6 col-md-offset-3">
      <form id="transform" class="well form-inline" v-on:submit="formSubmit">
        <input class="form-control" v-model='textToTranslate' type="text" name="" placeholder="输入要翻译的内容">
        <select class="form-control" v-model="language">
          <option value="en">English</option>
          <option value="ru">Russian</option>
          <option value="ko">Korean</option>
          <option value="ja">Janpense</option>
        </select>
        <input class="btn" type="submit" name="翻译">
      </form>
    </div>
  </div>
</template>

<script>
export default {
  name: 'TranslateForm',
  data:function(){
    return {
      textToTranslate: '',
      language: ''
    }
  },
  methods: {
    formSubmit: function(e){
      //alert(this.textToTranslate);
      this.$emit("formSubmit",this.textToTranslate,this.language)
      e.preventDefault();
    },
    created:function(){
      this.language = "en";
    }
  }
}
</script>

<style>
#transform{
  border:1px solid #ccc;
  border-radius: 10px;
}
</style>
