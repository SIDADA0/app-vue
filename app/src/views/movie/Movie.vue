<template>
    <div>
        <ul>
            <li @click="gotoDetail(movie.id)" class="movie" v-for="movie in movieList" :key="movie.id">
                <div class="movie-img">
                    <img :src="movie.images.large" alt="">
                </div>
                <div class="movie-info">
                    <div class="movie-info-title">{{movie.title}}</div>
                    <div> 观众评分：<span class="movie-info-average">{{movie.rating.average}}</span></div>
                    <div class="movie-info-star">主演：
                        <span v-for="item in movie.casts" :key="item.id">{{item.name}}&nbsp;</span>
                    </div>
                </div>
            </li>
        </ul>
        <div class="end" v-show="isEnd">
            <h3>您已加载全部场次...</h3>
        </div>
        <div class="loading" v-show="isLoading">
            <img src="@/assets/img/loading2.gif" alt="">
        </div>
    </div>
</template>


<script>
import axios from 'axios';

export default {
    data(){
        return{
            movieList:[],
            isLoading: true,
            isEnd:false
        };
    },
    methods:{
            getData() {
                let url1 ="https://bird.ioliu.cn/v2?url=https://api.douban.com/v2/movie/top250?start=0&count=5";
                // let url2 = "https://api.myjson.com/bins/pb8vw";
                let url2 ="https://api.myjson.com/bins/17ybu4";
                this.isLoading = true;
                axios.get(url2).then(res =>{
                    // console.log(
                    //     res.data.subjects.slice(
                    //     this.movieList.length,
                    //     this.movieList.length + 5
                    // )
                // );
                let getList = res.data.subjects.slice(
                    this.movieList.length,
                    this.movieList.length + 5
                );
                if (getList.length < 5) {
                    this.isEnd = true;
                }
                this.movieList = this.movieList.concat(getList);
                this.isLoading = false;
                });
            },
            gotoDetail(movieId){
                this.$router.push(`moviedetail/${movieId}`);
            }
    },
    created() {
        this.$emit('selectTab','movie');
        this.getData();
    },
    mounted () {
        window.onscroll =() => {
            let mi = document.documentElement.scrollTop || document.body.scrollTop;
            let scrollTop = Math.ceil(mi);
            let scrollHeight = Math.ceil(document.documentElement.scrollHeight);
            let clientHeight = document.documentElement.clientHeight;
            console.log(scrollHeight, scrollTop, clientHeight);
            if(scrollHeight == scrollTop +clientHeight && !this.isEnd){
                this.getData();
            }
        };
    }
};
</script>

<style lang="scss" scoped>
.movie {
    background-color: papayawhip;
    display: flex;
    padding: 0.2rem;
    border-bottom: 0.02rem solid #ccc;
    &-img {
    flex-grow: 1;
    width: 0;
    img {
    width: 100%;
    }
    }
    &-info {
    flex-grow: 3;
    width: 0;
    margin-left: 0.2rem;
    &-title {
    color: #333;
    font-weight: 700;
    font-size: 0.34rem;
    }
    &-average {
    font-weight: 700;
    color: #faaf00;
    // margin: 0 2rem;
    }

    &-star {
    color: #666;
    font-size: 0.26rem;
    }
}
}

.loading {
    text-align: center;
    position: fixed;
    bottom: 1rem;
    width: 100%;
    img {
    width: 3rem;
    }
}

.end {
    text-align: center;
}
</style>



