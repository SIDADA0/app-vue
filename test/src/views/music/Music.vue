<template>
    <h1>music</h1>
</template>


<script>
import Player from '@/components/Player.vue';
import axios from 'axios';
    export default {
        data(){
            return{
                musicList : ["musicList"],
            };
        },
        created() {
            this.$emit('selectTab','music');
            axios.get('/data/musicdata.json').then(res =>{
                this.musicList = res.data.musicData;
            });
        },
        components:{
            Player,
        },
    }
</script>

<style lang="scss" scoped>

</style>

