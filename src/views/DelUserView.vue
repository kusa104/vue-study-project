<template>
    <div>
        <p>회원삭제</p>
        <p>token : <input type="text" v-model="token"></p>
        <button @click="DelUser">탈퇴</button>
    </div>
</template>

<script>
    import axios from "axios"

    export default {

        data : () => ({
            id : '',
            pwd : '',
            token : '',
        }),

        methods : {
            DelUser() {
                axios.post('https://api.devcury.kr/api/auth/user', {
                    headers : {
                        Authorization: `Bearer ${this.token}`,
                    }
                }).then(response => {   
                    if(response.status === 200){
                        alert('유저삭제');
                    }
                }).catch(error=>{
                    alert(error.response.data.error);
                });
            }
        }
    }
</script>

<style scoped>

</style>