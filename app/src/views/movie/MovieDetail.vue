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
<style lang="scss" scoped>
*{
    // background-color: alpha($color: palegoldenrod)
    background-image: url(http://img.hb.aicdn.com/ff047fdb28dca60654c71efbccf9d0d05a80d67526cb0-mhbQfS_sq320) ;
}
.title{
    width: 100%;
    height: 2rem;
    text-align: center;
    color: red;
    background-color: peachpuff;
    &-content{
        position: fixed;
        top: 2rem;
        width: 100% ;
        height: 100%;
        background-color: papayawhip;
        span{
            width: 60%;
            color: rebeccapurple;
            display: block;
            margin: 2rem auto;
        }
    }
}
</style>

