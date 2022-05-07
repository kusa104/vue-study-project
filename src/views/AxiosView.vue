<template>
    <div>
        <select v-model="type">
          <option value="1">웹문서</option>
          <option value="2">이미지</option>
        </select>
        <input type="text" v-model="search" @keyup.enter="callKakao">
        <button @click="callKakao">검색</button>

        <div v-if="type == '1'">
            <table>
                <tr>
                    <th>제목</th>
                    <th>내용</th>
                </tr>
                <tr v-for="(item, index) in list" :key="index">
                    <td>
                        <a :href="item.url" target='_blank'>
                            <span v-html="item.title"></span>
                        </a>
                    </td>
                    <td>
                        <span v-html="item.contents"></span>
                    </td>
                </tr>
            </table>
        </div>
        <div v-else>
            <table>
                <tr>
                    <th>제목</th>
                    <th>이미지</th>
                </tr>
                <tr v-for="(item, index) in list" :key="index">
                    <td>
                        <a :href="item.url" target='_blank'>
                            <span v-html="item.collection"></span>
                        </a>
                    </td>
                    <td>
                        <span><img :src="item.image_url" /></span>
                    </td>
                </tr>
            </table>
        </div>        

    </div>
</template>

<script>
    import axios from "axios";

    export default {

        data : ()=> ({
            type : '1',
            search : '',
            list : []
        }),

        methods : {
            callKakao(){
                switch(this.type){
                    case '1':
                        this.callData();
                        break;
                    case '2':
                        this.callImg();
                        break;
                }
            },
            callData(){
                axios.get(`https://dapi.kakao.com/v2/search/web?query=${this.search}`, {
                    headers : {
                        Authorization: `KakaoAK ${process.env.VUE_APP_KAKAO_KEY}`
                    }
                }).then(response => {
                    console.log(response);
                    this.list = response.data.documents;
                }).catch(error => {
                    console.error(error);
                })
            },
            callImg(){
                axios.get(`https://dapi.kakao.com/v2/search/image?query=${this.search}`, {
                    headers : {
                        Authorization: `KakaoAK ${process.env.VUE_APP_KAKAO_KEY}`
                    }
                }).then(response => {
                    console.log(response);
                    this.list = response.data.documents;
                }).catch(error => {
                    console.error(error);
                })
            },
        }
    }
</script>

<style scoped>

</style>