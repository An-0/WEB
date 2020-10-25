<template>
  <div>
      User
      <h3>UserList</h3>
      <table border="1">
          <tr>
              <td>ID</td>
              <td>姓名</td>
              <td>生日</td>
              <td>个人信息</td>
              <td>操作</td>
          </tr>
          <tr v-for="(user, index) in users_list" :key="user.id">
              <td>{{user.id}}</td>
              <td>{{user.username}}</td>
              <td>{{user.bir}}</td>
              <td>{{user.content}}</td>
              <td><a href="javascript:;" @click="delUser(index)">删除</a>|<a href="javascript:;" @click="detail(index)">查看</a></td>
          </tr>
      </table>
      <hr>
      username：<input type="text" v-model="username"><br>
      bir：<input type="text" v-model="bir"><br>
      content： <input type="text" v-model="content"><br>
      <button @click="adduser">确认</button>
  </div>
</template>

<script>
export default {
    name:"User",
    data(){
        return {
            username:"",
            bir:"",
            content:"",
            users_list: localStorage.users_list ? JSON.parse(localStorage.users_list) : [],
        }

    },
    methods:{
        adduser(){
            // localStorage.clear()
            console.log(this.users_list)
            if(this.users_list.length===0){
                var id=1
            }
            else{
                id=this.users_list[0]["id"]++
            }
            this.users_list.push({
                "id":id,
                "username":this.username,
                "bir":this.bir,
                "content":this.content,
            })
            localStorage.users = JSON.stringify(this.users_list);
            this.username = "";
            this.bir = "";
            this.content = "";
        },
        delUser(index){
            this.users_list.splice(index, 1)
            localStorage.users_list = JSON.stringify(this.users_list)

        },
        detail(index) {
            // console.log(index)
            this.$router.push("/detail/" + index)
        },
    }

}
</script>

<style>

</style>