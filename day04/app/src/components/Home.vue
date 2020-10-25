<template>
  <div>
    <input type="text" v-model="msg" />
    <button @click="add_note">添加留言</button>

    <ul>
      <li v-for="(note, index) in msg_list" :key="index">
        {{ note }}
        <a href="javascript:;" @click="delNote(index)">删除</a>
        </li>
    </ul>
  </div>
</template>

<script>
export default {
    name:"Home",
    data: function(){
        return {
            msg: "",
            // 哦按段localStorage是否有值  有值则显示 如果没有 则设置成空数组
            msg_list: localStorage.msg_list ? JSON.parse(localStorage.msg_list) : [],
        }
    },
        methods: {
            add_note() {
                let msg = this.msg;
                if (msg){
                    this.msg_list.push(this.msg);
                    // 将用户发表的留言储存到localstorage
                    // 储存前将数据进行序列化
                    localStorage.msg_list = JSON.stringify(this.msg_list);
                    this.msg = "";
                }
            },
            delNote(index){
              console.log(this.msg_list)
              this.msg_list.splice(index, 1)
              localStorage.msg_list = JSON.stringify(this.msg_list)
              console.log(this.msg_list)

            }
        }
};
</script>

<style>
</style>