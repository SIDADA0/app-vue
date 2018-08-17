    <template>
        <swipe class="my-swipe">
            <swipe-item class="slide1"></swipe-item>
            <swipe-item class="slide2"></swipe-item>
            <swipe-item class="slide3"></swipe-item>
            <swipe-item class="slide4"></swipe-item>
            <swipe-item class="slide5"></swipe-item>
            <swipe-item class="slide6"></swipe-item>
        </swipe>
    </template>


    <script>
    import 'vue-swipe/dist/vue-swipe.css';
    import { Swipe, SwipeItem } from "vue-swipe";
    export default {
    created() {
        this.$emit("switchTab", "book");
    },
    components: {
        swipe: Swipe,
        "swipe-item": SwipeItem
    }
    };
    </script>

    <style lang="scss" scoped>
    .my-swipe {
    height:9.38rem;
    color: #fff;
    font-size: 30px;
    text-align: center;
    }

    .slide1 {
    background-image: url(http://img.hb.aicdn.com/b00442f97eb37d86dbde6222d3b0f518e2323bd1f382b-w7LidH_fw658);
    // color: #fff;
    background-size: cover;
    }

    .slide2 {
    background-image: url(http://img.hb.aicdn.com/35de30104492e75a5b1e498218deffbcf61de02c119073-BjRDdH_fw658);
    color: #000;
    background-size: cover;
    }

    .slide3 {
    background-image: url(http://img.hb.aicdn.com/e870345243a6523036b2d18fa077f8f16f29267095cc3-1TNEKs_fw658);
    color: #fff;
    background-size: cover;
    }
    
    .slide4 {
    background-image: url(http://img.hb.aicdn.com/cf9ec2a48f19075d0e71376205b4acae2615a188142afa-lsHIpO_fw658);
    color: #fff;
    background-size: cover;
    }
    .slide5 {
    background-image: url(http://img.hb.aicdn.com/f4103836c2b384b55521130b798362b0591e8bf61079a1-jK2vhJ_fw658);
    color: #fff;
    background-size: cover;
    }
    .slide6 {
    background-image: url(http://img.hb.aicdn.com/60012cfa0fb3c3e6e07209eead90da469fc454792badc-DsTeZc_fw658);
    color: #fff;
    background-size: cover;
    }
    </style>
