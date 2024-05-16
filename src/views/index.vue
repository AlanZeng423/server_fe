<template>
    <h1>云边协同大模型多模态生成系统</h1>
    <!-- <div class="button-container">
      <button class="styled-button">Server 1</button>
      <button class="styled-button">Server 2</button>
      <button class="styled-button">Server 3</button>
      <button class="styled-button">Server 4</button>
      <button class="styled-button">Server 5</button>
    </div> -->
    <div class="common-layout">
        <el-button>Server 1</el-button>
        <el-button>Server 2</el-button>
        <el-button>Server 3</el-button>
        <el-button>Server 4</el-button>
        <el-button>Server 5</el-button>
        <!-- <el-button type="primary">Primary</el-button>
        <el-button type="success">Success</el-button>
        <el-button type="info">Info</el-button>
        <el-button type="warning">Warning</el-button>
        <el-button type="danger">Danger</el-button>  -->
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
  export default {
    name: 'HomePage'
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
  </style>
  