<template>
  <div class="about">
    <h1>This is an about page</h1>
    <button @click="test()">getMember</button>
    <button @click="createMember()">createMember</button>
    <button @click="changeMemberName()">changeMemberName</button>
    <div>{{msg}}</div>
  </div>
</template>
<script>

export default {
  name: 'App',
  data(){
    return {
      msg : ''
    }
  },
  methods: {
    test(){
      this.axios.get("/api/member")
      .then(res => {
        this.msg = res.data;
      })
      .catch((e) =>{
        console.log(e);
      });
    },
    createMember(){
      this.axios.post("/api/member", {user_id : "id", password:"pwd", name:"name"})
        .then(res => {
          this.content = res.data;
        })
        .catch(e =>{
          console.log(e);
        });
    },
    changeMemberName(){
      this.axios.put("/api/member/name/2", {name:"13"})
        .then(res => {
          this.content = res.data;
        })
        .catch(e =>{
          console.log(e);
        });
    },
  },

}
</script>