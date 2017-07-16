<template>
  <div id="app">
    <input type="button" value="切换裁切" @click="canCrop=!canCrop">
    <editor ref="myTextEditor"
            :fileName="'myFile'"
            :canCrop="canCrop"
            :uploadUrl="uploadUrl"
            v-model="content"></editor>
    <div v-html="content"></div>
  </div>
</template>

<script>
import editor from './components/Quilleditor.vue'
export default {
  name: 'app',
  data(){
    return {
      canCrop:false,
      /*测试上传图片的接口，返回结构为{url:''}*/
      uploadUrl:'http://localhost:4000/api/upload',
      content:''
    }
  },
  components: {
    editor
  }
}
</script>

<style>
</style>
