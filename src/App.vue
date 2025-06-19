<template>
  <div v-if="!hasEntered">
    <input
      v-model="username"
      @keyup.enter="confirmName"
      placeholder="이름을 입력하세요"
    />
    <button @click="confirmName">Enter</button>
  </div>
  
  <!-- v-if="hasEntered" 이 조건에 따라 화면이 갈림 -->
  <div v-if="hasEntered"> 
    <p>Hello, {{ username }}!</p>

    <input
      v-model="newTask"
      @keyup.enter="addTask"
      placeholder="할 일을 입력하세요"
    />

    <ul>
      <li v-for="(task, index) in tasks" :key="index">
        {{ task }}
      </li>
    </ul>
  </div>
</template>

<script>
export default { //이 파일이 vue 컴포넌트라고 알려주는 코드
  name: 'App', //컴포넌트의 이름 (디버깅/확장에 유용)
  data(){
    return {
      username : '',
      hasEntered: false, //초기값
      newTask: '',
      tasks: [],
    }
  },
  methods: {
    confirmName() {
      if (this.username.trim()) {
        this.hasEntered = true;
      }
    }
  },
  addTask() {
    if (this.newTask.trim()) {
      this.tasks.push(this.newTask);
      this.newTask = '';
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
