<template>
  <!-- eslint-disable -->
  <div class="main-container">
    <div class="header">
      <div class="avatar"><div class="tju"></div></div>
      <span class="cloud-edge">云边协同大模型多模态生成系统</span>
    </div>
    <div class="flex-row-f">
      <div class="two-columns">
        <div class="input">
          <span class="user-input">用户输入</span>
          <textarea class="field" v-model="textarea" placeholder="请输入您的需求或上传文件"></textarea>
          <!-- <el-input
              class="field"
              style="height: auto; width: auto;"
              v-model="textarea"
              type="textarea"
              placeholder="请输入您的需求或上传文件 input"
          /> -->
        </div>
        <div class="frame">
          <button class="submit-button" @click="handleTextSubmit"><span class="submit">提交</span></button>
          <button class="button" @click="triggerFileSelect">
            <span class="select-file">选择文件</span>
          </button>
          <input type="file" ref="fileInput" @change="handleFileUpload" style="display: none;" />
        </div>
        <div class="output">
          <span class="output-text">输出</span>
          <div class="field-1"><div class="output-content">{{output_content}}</div></div>
        </div>
      </div>
      <div class="server">
        <div class="flex-row-dc">
          <div class="server-div"></div>
          <div class="server-div-2"></div>
          <div class="server-div-3"></div>
          <div class="server-div-4"></div>
        </div>
        <div class="flex-row-c">
          <!-- <div class="arrow-div"></div> -->
          <span class="server-span">服务器1</span>
          <span class="server-2">服务器2</span>
          <span class="server-3">服务器3</span>
          <span class="server-4">服务器4</span>
          <div class="server-5"></div>
        </div>
        <span class="main-server">主服务器</span>
      </div>
    </div>
  </div>
</template>

<script>
import { ref } from 'vue';

export default {
  name: 'HomePage',
  setup() {
    const textarea = ref('');
    const output_content = ref('HAHA');
    const fileInput = ref(null);

    //
    const triggerFileSelect = () => {
      if (fileInput.value) {
        fileInput.value.click();
      }
    };

    const handleTextSubmit = async () => {
      const formData = new FormData();

      // 将文本内容保存为 Blob 并添加到 FormData
      const textBlob = new Blob([textarea.value], { type: 'text/plain' });
      formData.append('textFile', textBlob, 'input.txt');

      alert(textarea.value);
      // console.


      try {
        const response = await fetch('http://your-backend-endpoint/upload', {
          method: 'POST',
          body: formData
        });
        if (response.ok) {
          alert('文件上传成功');
        } else {
          alert('文件上传失败');
        }
      } catch (error) {
        alert('上传过程中出现错误: '+error);
      }
    };

    const handleFileUpload = async (event) => {
      const file = event.target.files[0];
      if (file) {
        console.log('上传的文件:', file.name);
        const formData = new FormData();
        formData.append('file', file);
        try {
          const response = await fetch('http://your-backend-endpoint/upload', {
            method: 'POST',
            body: formData
          });
          if (response.ok) {
            console.log('文件上传成功');
          } else {
            console.error('文件上传失败');
          }
        } catch (error) {
          console.error('上传过程中出现错误:', error);
        }
      }
    }
    // 
    return { 
      textarea,
      fileInput,
      output_content,
      handleFileUpload,
      handleTextSubmit,
      triggerFileSelect
    };
  }
};
</script>

<style src="./index.css"></style>
