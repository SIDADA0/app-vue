<template>
    <div>
        <h1 class="head">{{detail.title}}</h1>
        <p class="head-content">{{detail.summary}}</p>
    </div>
</template>

<script>
import axios from "axios";
    export default {
        data(){
            return {
                detail: {}
            }
        },
    created() {
        let url = `https://bird.ioliu.cn/v2?url=https://api.douban.com/v2/movie/subject/${
        this.$route.params.movieId
        }`;
        axios.get(url).then(res => {
        console.log(res);
        this.detail = res.data;
        });
    }
    };
</script>

<style lang="scss" scoped>
*{
    background-color: alpha($color: palegoldenrod)
}
.head{
    width: 100%;
    height: 2rem;
    text-align: center;
    background-color: peachpuff;
    &-content{
        width: 100% ;
        height: 100%;
        background-color: papayawhip;
    }
}
</style>
