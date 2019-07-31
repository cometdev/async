<template>
  <div>
    <button @click="fetchUser">get user</button>
    <!-- TODO: 버튼을 눌렀을 때 아래와 같은 동작을 구현해 주세요. -->
    <ol>
      <li>`url1`을 이용해서 사용자 정보를 요청</li>
      <li>호출 받은 사용자 정보의 id 값이 1인지 체크</li>
      <li>id가 맞으면 `url2`로 할 일 정보를 요청</li>
      <li>할 일 정보는 콘솔에 출력 또는 화면에 표시</li>
    </ol>
    
    <div>{{todolist}}</div>
  </div>
</template>

<script>
import axios from 'axios';

const url1 = 'https://jsonplaceholder.typicode.com/users/1';
const url2 = 'https://jsonplaceholder.typicode.com/todos/1';

export default {
  data() {
    return {
      todolist: ''
    }
  },
  methods: {
    async fetchUser() {
      let vm = this;

      // axios.get(url1).then(response => {
      //   let data = response.data;

      //   if (data.id === 1) {
      //     axios.get(url2).then(response => {
      //       let data = response.data;
      //       this.todolist = data.title;
      //     }).catch(error => {
      //     });
      //   }
      // }).catch(error => {
      // });

      let res = await axios.get(url1);

      if (res.data.id === 1) {
        let res2 = await axios.get(url2);
        this.todolist = res2.data.title;
      }
    }
  },
}
</script>

<style>

</style>
