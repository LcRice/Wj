<template>
    <div>
        <span>
            用户名：
        </span>
        <input name="username" placeholder="请输入用户名" type="text" v-model="LoginForm.username"/>
        <br/><br/>
        <span>
            密码：
        </span>
        <input name="password" placeholder="请输入用户名" type="text" v-model="LoginForm.password"/>
        <br/><br/>
        <button name="submit" v-on:click="login" >登录</button>
    </div>
</template>

<script>
    export default {
        name: "LoginPage",
        data (){
            return {
                LoginForm : {
                    username : '',
                    password : ''
                },
                responseResult : []
            }
        },
        methods: {
            login (){
                this.$axios.port('/login',
                    {
                        username: this.LoginForm.username,
                        password: this.LoginForm.password
                    }
                ).then(
                    successResponse =>{
                        if(successResponse.data().return_code === 200){
                            this.$router.replace({path:'/index'})
                        }
                    }
                ).catch(failResponse =>{

                })
            }
        }
    }
</script>

<style scoped>

</style>