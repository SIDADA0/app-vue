<template>
    <ul class="clearfix">
        <li @click="gotoDetail(index)" class="photo" v-for="(photo,index) in $store.state.photoList" :key="photo.src">
            <img :src="photo.src" alt="">
        </li>
    </ul>
</template>


<script>
import axios from 'axios';
export default {
    data(){
        return{};
    },
    created() {
    this.$emit("switchTab", "photo");
    axios.get("/data/photodata.json").then(res => {
        this.$store.commit('setPhotoList', res.data.photoData);
    });
    },
    methods:{
        gotoDetail(index){
            this.$router.push(`/photodetail/${index}`);
        }
    }
};
</script>

<style lang="scss" scoped>
.clearfix{
    content: '';
    display: block;
    clear: both;
}
.photo{
    background: papayawhip;
    width: 2.6rem;
    height: 3.3rem;
    float: left;
    padding: 0.8rem 0.3rem;
    // overflow-X: scroll;
}
</style>

