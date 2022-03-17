<template>
  <div class="hello">
    <h1>로그인</h1>
    
    <form @submit.prevent="login()">
      <input type="text" placeholder="username" v-model="user">
      <input type="password" placeholder="password" v-model="password">
      <button type="submit">Login</button>
    </form>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data() {
    return {
      user : 'id1',
      password : 'pwd1'
    }
  },
  methods: {
    login(){
      try {
        console.log(this.user, this.password);
        this.axios.post('/login', {username: this.user, password: this.password})
      }
      catch (e) {
        console.log(e);
      }
    }
  },
}
</script>

