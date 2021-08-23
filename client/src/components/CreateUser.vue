<template>
<div>
    <h1>Create User</h1>
    <form v-on:submit.prevent = "createUser">
        <p>nameDog: <input type="text" v-model="user.name"></p>
        <p>dog breed: <input type="text" v-model="user.lastname"></p>
        <p>Email Dog: <input type="text" v-model="user.email"></p>
        <p>Birthday: <input type="text" v-model="user.birthday"></p>
        <p>how to raise: <input type="text" v-model="user.password"></p>
        <p><button type="submit">create user</button></p>
    </form>
    <hr>
    <div>
        <p>nameDog: {{user.name}}</p>
        <p>dog breed: {{user.lastname}}</p>
        <p>Email Dog: {{user.email}}</p>
        <p>Birthday: {{user.birthday}}</p>
        <p>how to raise: {{user.password}}</p>
    </div>
</div>
</template>
<script>
import UsersService from '@/services/UsersService'

export default {
    data(){
        return{
            user:{
                name: '',
                lastname: '',
                email: '',
                birthday: '',
                password: '',
                status: 'active'
            }
        }
    },
    methods:{
        async createUser(){
            try{
                await UsersService.post(this.user)
                this.$router.push({
                    name: 'users'
                })
            }catch(error){
                console.log(error)
            }
        }
    }    
}
</script>
<style scoped>


</style>