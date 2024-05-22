<template>
    <h1>云边协同大模型多模态生成系统</h1>
    <!-- <div class="button-container">
      <button class="styled-button">Server 1</button>
      <button class="styled-button">Server 2</button>
      <button class="styled-button">Server 3</button>
      <button class="styled-button">Server 4</button>
      <button class="styled-button">Server 5</button>
    </div> --> 
    <div class="server_container">
      <div class="container">
        <div class="servers">
          <div class="server" v-for="server in servers" :key="server.id">
            <img :src="server.status === 'on' ? serverOnImage : serverOffImage" :alt="`服务器${server.status}状态`">
            服务器 {{ server.id }}
            <button class="toggle-btn" @click="toggleServer(server.id)">
              {{ server.status === 'on' ? '关闭' : '开启' }}
            </button>
            
          </div>
        </div>
      </div>
      <br><br><br>
      <div class="container">
        <div class="main_server">
          <img :src="main_server.status === 'on' ? serverOnImage : serverOffImage" :alt="`服务器${main_server.status}状态`">
          主服务器
        </div>
      </div>
    </div>
    <br>
    <div>
        <el-button type="primary" size="large">Main Server</el-button>
    </div>
    <br>
    <div class="common-layout">
        是否使用已有用户数据：
        <el-button-group>
            <el-button type="primary" plain>Previous Page</el-button>
            <el-button color="#626aef" plain>Next Page</el-button>
        </el-button-group>
    </div>
    <br>
    <div class="button-container">
        <el-text class="mx-1">Default</el-text>
    </div>
  </template>
  
<script>
  // Vue 3 script setup
  import { ref } from 'vue';
  import serverOnImage from '@/assets/server_on.png'; // 确保图片在 assets 目录下
  import serverOffImage from '@/assets/server_off.png'; // 确保图片在 assets 目录下

  export default {
    name: 'HomePage',
    setup() {
      const servers = ref([
        { id: 1, status: 'on' },
        { id: 2, status: 'on' },
        { id: 3, status: 'on' },
        { id: 4, status: 'on' },
        { id: 5, status: 'on' }
      ]);
      
      const main_server = ref({
        id: 0, status: 'on'
      })

      const toggleServer = (serverId) => {
        const server = servers.value.find(s => s.id === serverId);
        if (server) {
          server.status = server.status === 'on' ? 'off' : 'on';
        }
      };
    
      return {
        servers,
        main_server,
        serverOffImage,
        serverOnImage,
        toggleServer
      }
    }
  }
  
  </script>
  
  <style>
  .button-container {
    display: flex;
    flex-direction: row;
    justify-content: space-around;
    padding: 20px;
    background-color: #f4f4f4;
    border-radius: 10px;
    margin: 20px;
  }

  .server_container {
    background-color: #f4f4f4;
  }
  
  .styled-button {
    padding: 10px 20px;
    font-size: 16px;
    color: #fff;
    background-color: #007BFF;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    transition: background-color 0.3s, transform 0.3s;
  }
  
  .styled-button:hover {
    background-color: #0056b3;
    transform: translateY(-2px);
  }
  
  .styled-button:active {
    background-color: #004085;
    transform: translateY(1px);
  }
  .container {
    display: flex;
    justify-content: center;
    align-items: center;
    /* height: 100vh; 使容器占满整个视口高度 */
  }
  .servers {
    display: flex;
    justify-content: space-around;
    align-items: center;
    /* flex-wrap: wrap; */
    gap: 40px;
  }

  .server {
    text-align: center;
  }

  .server img {
    width: 80px; /* 调整图片宽度 */
    height: auto;
  }

  .main_server img {
    width: 120px; /* 调整图片宽度 */
    height: auto;
  }


  .toggle-btn {
    margin-top: 15px;
    padding: 5px 10px;
    cursor: pointer;
    background-color: #143252;
    color: white;
    border: none;
    border-radius: 4px;
  }
</style>
  