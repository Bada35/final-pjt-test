<template>
    <div>
        <h1>홈뷰</h1>
    </div>

</template>
  
<script>
import axios from 'axios';

export default {
    data() {
        return {
            responseData: null,
        };
    },
    methods: {
        fetchData() {
            const url = 'http://api.koreafilm.or.kr/openapi-data2/wisenut/search_api/search_xml2.jsp';
            const params = {
                collection: 'kmdb_new2',
                detail: 'N',
                director: '박찬욱',
                ServiceKey: '인증키값'
            };

            axios.get(url, { params })
                .then(response => {
                    this.responseData = response.data;
                })
                .catch(error => {
                    console.error("API 요청 오류:", error);
                });
        }
    },
    mounted() {
        this.fetchData();
    }
};
</script>
  
<style scoped>

</style>
  