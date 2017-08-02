<template>
    <div>
        <quill-editor v-model="content"
                     ref="myTextEditor"
                     :options="editorOption"
                     @change="onChange"
        >
            <div id="toolbar" slot="toolbar">
                <span class="ql-formats"><button type="button" class="ql-bold"></button></span>
                <span class="ql-formats"><button type="button" class="ql-italic"></button></span>
                <span class="ql-formats"><button type="button" class="ql-underline"></button></span>
                <span class="ql-formats"><button type="button" class="ql-strike"></button></span>
                <span class="ql-formats"><button type="button" class="ql-blockquote"></button></span>
                <span class="ql-formats"><button type="button" class="ql-code-block"></button></span>
                <span class="ql-formats"><button type="button" class="ql-header" value="1"></button></span>
                <span class="ql-formats"><button type="button" class="ql-header" value="2"></button></span>
                <span class="ql-formats"><button type="button" class="ql-list" value="ordered"></button></span>
                <span class="ql-formats"><button type="button" class="ql-list" value="bullet"></button></span>
                <span class="ql-formats"><button type="button" class="ql-script" value="sub"></button></span>
                <span class="ql-formats"><button type="button" class="ql-script" value="super"></button></span>
                <span class="ql-formats"><button type="button" class="ql-indent" value="-1"></button></span>
                <span class="ql-formats"><button type="button" class="ql-indent" value="+1"></button></span>
                <span class="ql-formats"> <button type="button" class="ql-direction" value="rtl"></button></span>

      <span class="ql-formats"><select class="ql-size">
        <option value="small"></option>
        <option selected></option>
        <option value="large"></option>
        <option value="huge"></option>
      </select></span>
      <span class="ql-formats"><select class="ql-header">
        <option value="1"></option>
        <option value="2"></option>
        <option value="3"></option>
        <option value="4"></option>
        <option value="5"></option>
        <option value="6"></option>
        <option selected="selected"></option>
      </select></span>
      <span class="ql-formats"><select class="ql-color">
        <option selected="selected"></option>
        <option value="#e60000"></option>
        <option value="#ff9900"></option>
        <option value="#ffff00"></option>
        <option value="#008a00"></option>
        <option value="#0066cc"></option>
        <option value="#9933ff"></option>
        <option value="#ffffff"></option>
        <option value="#facccc"></option>
        <option value="#ffebcc"></option>
        <option value="#ffffcc"></option>
        <option value="#cce8cc"></option>
        <option value="#cce0f5"></option>
        <option value="#ebd6ff"></option>
        <option value="#bbbbbb"></option>
        <option value="#f06666"></option>
        <option value="#ffc266"></option>
        <option value="#ffff66"></option>
        <option value="#66b966"></option>
        <option value="#66a3e0"></option>
        <option value="#c285ff"></option>
        <option value="#888888"></option>
        <option value="#a10000"></option>
        <option value="#b26b00"></option>
        <option value="#b2b200"></option>
        <option value="#006100"></option>
        <option value="#0047b2"></option>
        <option value="#6b24b2"></option>
        <option value="#444444"></option>
        <option value="#5c0000"></option>
        <option value="#663d00"></option>
        <option value="#666600"></option>
        <option value="#003700"></option>
        <option value="#002966"></option>
        <option value="#3d1466"></option>
      </select></span>
     <span class="ql-formats"> <select class="ql-background">
        <option value="#000000"></option>
        <option value="#e60000"></option>
        <option value="#ff9900"></option>
        <option value="#ffff00"></option>
        <option value="#008a00"></option>
        <option value="#0066cc"></option>
        <option value="#9933ff"></option>
        <option selected="selected"></option>
        <option value="#facccc"></option>
        <option value="#ffebcc"></option>
        <option value="#ffffcc"></option>
        <option value="#cce8cc"></option>
        <option value="#cce0f5"></option>
        <option value="#ebd6ff"></option>
        <option value="#bbbbbb"></option>
        <option value="#f06666"></option>
        <option value="#ffc266"></option>
        <option value="#ffff66"></option>
        <option value="#66b966"></option>
        <option value="#66a3e0"></option>
        <option value="#c285ff"></option>
        <option value="#888888"></option>
        <option value="#a10000"></option>
        <option value="#b26b00"></option>
        <option value="#b2b200"></option>
        <option value="#006100"></option>
        <option value="#0047b2"></option>
        <option value="#6b24b2"></option>
        <option value="#444444"></option>
        <option value="#5c0000"></option>
        <option value="#663d00"></option>
        <option value="#666600"></option>
        <option value="#003700"></option>
        <option value="#002966"></option>
        <option value="#3d1466"></option>
      </select></span>
      <span class="ql-formats"><select class="ql-font">
        <option selected="selected"></option>
        <option value="serif"></option>
        <option value="monospace"></option>
      </select></span>
      <span class="ql-formats">
        <select class="ql-align">
        <option selected="selected"></option>
        <option value="center"></option>
        <option value="right"></option>
        <option value="justify"></option>
      </select>
      </span>
      <span class="ql-formats">
          <button type="button" class="ql-clean"></button>
      </span>
      <span class="ql-formats">
          <button type="button" class="ql-link"></button>
      </span>
      <span class="ql-formats">
          <button type="button" @click="imgClick">
            <svg viewBox="0 0 18 18">
                <rect class="ql-stroke" height="10" width="12" x="3" y="4"></rect>
                <circle class="ql-fill" cx="6" cy="7" r="1"></circle>
                <polyline class="ql-even ql-fill" points="5 12 5 11 7 9 8 10 11 7 13 9 13 12 5 12"></polyline>
            </svg>
          </button>
      </span>
       <span class="ql-formats">
           <button type="button" class="ql-video"></button>
       </span>
     </div>
        </quill-editor>
        <crop-upload
                   v-model="showCrop"
                   :width="width"
                   :height="height"
                   :fileName="fileName"
                   :uploadUrl="uploadUrl"
                   @uploadSuccess="onUploadSuccess"
                   ></crop-upload>
    </div>
</template>
<script>
    import {quillEditor} from 'vue-quill-editor'
    import CropUpload from './CropUpload';
    export default {
        props: {
            /*编辑器的内容*/
            value: {
                type: String
            },
            /*上传图片的地址*/
            uploadUrl: {
                type: String
            },
            /*上传图片的file控件name*/
            fileName: {
                type: String
            },
            /*图片大小*/
            maxSize:{
                type:Number,
                default:400//kb
            },
            /*使用使用裁切*/
            canCrop:{
                type:Boolean,
                default:false
            },
            /*裁切的最小尺寸*/
            width:{
                type:Number,
                default:200
            },
           /*裁切的最小尺寸*/
            height:{
                type:Number,
                default:200
            }
        },
        data() {
            return {
                content: '',
                editorOption: {
                    modules: {
                        toolbar: '#toolbar'
                    }
                },
              /*显示裁切控件*/
                showCrop:false
            }
        },
        methods: {
            onChange(){
                this.$emit('input', this.content)
            },
            /*选择上传图片切换*/
            onFileChange(e){
                var fileInput = e.target;
                if (fileInput.files.length == 0) {
                    return;
                }
                if (fileInput.files[0].size > 1024 * 1024 * this.maxSize) {
                    alert('图片过大');
                    return;
                }
              if (!this.uploadUrl) {
                console.log('no editor uploadUrl');
                return;
              }
              var self = this;
              var data = new FormData;
              data.append(this.fileName, fileInput.files[0],name);
              this.editor.focus();
              var xhr=new XMLHttpRequest();
              xhr.open('post',this.uploadUrl);
              xhr.responseType='json';
              xhr.send(data);
              xhr.onload=function () {
                if(xhr.status==200){
                  self.editor.insertEmbed(self.editor.getSelection().index, 'image', xhr.response.url);
                }
              }
            },
            /*裁切上传成功 res根据上传接口值获取*/
            onUploadSuccess:function (res) {
              this.editor.focus();
              this.editor.insertEmbed(this.editor.getSelection().index, 'image', res.url);
            },
            /*点击上传图片按钮*/
            imgClick() {
                if(this.canCrop){
                    this.showCrop=true;
                }else{
                  /*创建input file 不裁切，自己控制*/
                  var input = document.createElement('input');
                  input.type = 'file';
                  input.name = this.fileName;
                  input.accept = 'image/jpeg,image/png,image/jpg,image/gif';
                  input.onchange = this.onFileChange;
                  input.click();
                }
            },

        },
        computed: {
            editor() {
                return this.$refs.myTextEditor.quill;
            }
        },
        components: {
            quillEditor,
            CropUpload
        },
        mounted(){
            this.content = this.value;
        },
        watch: {
            'value'(newVal, oldVal) {
                if (this.editor) {
                    if (newVal !== this.content) {
                        this.content = newVal
                    }
                }
            },
        }
    }
</script>
