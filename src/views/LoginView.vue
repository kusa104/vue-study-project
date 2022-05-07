<template>
    <div>
        <p>로그인</p>
        <p>ID : <input type="text" v-model="id"></p>
        <p>PW : <input type="password" v-model="pwd"></p>
        <button @click="login">로그인하여 토큰 발급</button>
    </div>
</template>

<script>
    import axios from "axios"

    export default {
        data : () => ({
            id : '',
            pwd : '',
            token : ''
        }),
        methods : {
            login(){
                axios.post('https://api.devcury.kr/auth/user', {
                    id : this.id,
                    pwd : this.pwd,
                }).then(response => {   
                    if(response.status === 200){
                        this.token = response.data.token;
                        alert(response.data.token);
                    }
                }).catch(error=>{
                    alert(error.response.data.error);
                });
            },
        }
    }
</script>

<style scoped>

</style>