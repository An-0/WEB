<template>
 <div>
    id： {{user.id}}<br>
    姓名： {{user.username}}<br>
    年龄： {{user.bir}}<br>
    个人简介： {{user.content}}<br>
</div>
</template>

<script>
export default {
    name:"UserDetail",
    data() {
        return {
            index: '',
            user:'',
        }
    },
    beforeMount() {
        this.index = this.$route.params.id
        this.user = JSON.parse(localStorage.users_list)[this.index]
        console.log(this.user)
    }
}
</script>

<style>

</style>