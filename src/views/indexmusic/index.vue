<style scoped lang='stylus'>
h3 {
    font-weight: normal;
    font-size: 18px;
    height: 40px;
    line-height: 40px;
}

h3:before {
    content: "|";
    color: #C20C0C;
    background: #C20C0C;
    font-size: 15px;
    margin: 0 6px;
}

.albumList {
    ul {
        display: flex;
        flex-wrap: wrap;
        li {
            width: 33.3333%;
            padding:2px;
            box-sizing: border-box;
            img {
                width: 100%;
                display: block;
            }
            p {
                text-align: center;
                height: 26px;
                line-height: 26px;
                font-size: 14px;
            }
        }
    }
}

.recommend {
    li.cur {
        color: #c20c0c;
        .musicName {
            color: #c20c0c;
        }
        .musicSinger {
            color: #c20c0c;
        }
    }
    div.index {
        width: 50px;
        line-height: 50px;
        text-align: center;
    }
    div {
        height: 50px;
        .musicName {
            color: #4b4c4d;
            height: 20px;
            line-height: 25px;
            font-weight: bold;
            font-size: 16px;
        }
        .musicSinger {
            color: #888;
            font-size: 12px;
            height: 20px;
            line-height: 25px;
        }
    }
    .icon-bofang {
        font-size: 28px;
        line-height: 50px;
        height: 50px;
        width: 50px;
        text-align: center;
    }
}

</style>
<template>
    <div v-height="50" style="overflow-y:scroll;">
        <vui-swiper-x :imgArr="imgArr"></vui-swiper-x>
        <div class="albumList">
            <h3>推荐专辑</h3>
            <ul>
                <li v-for="(item,index) of album" @click="showAlbum(item,index)">
                    <img :src="item.albumImage">
                    <p>{{item.albumTitle}}</p>
                </li>
            </ul>
        </div>
        <div class="recommend">
            <h3>热门歌曲</h3>
            <ul>
                <li v-for="(item , index) in recommend" @click="playRecommend(recommend,index)" :class="{cur : index == $store.state.player.index && $store.state.player.albumIndex == null}" class="ovh">
                    <div class="fl index">{{index + 1}}</div>
                    <div class="fl">
                        <p class="musicName">{{item.musicName}}</p>
                        <p class="musicSinger">{{item.musicSinger}}</p>
                    </div>
                    <span class="iconfont icon-bofang fr"></span>
                </li>
            </ul>
        </div>
    </div>
</template>
<script>
import VuiSwiperX from "../../components/swiper.vue"

export default {
    data() {
        return {
            imgArr: [
            {
                url: "http://p1.music.126.net/zEHjTR7wFIWA8YZ4izSqgA==/109951163208687014.jpg" 
            },{
                url: "http://p1.music.126.net/x7oXavnkbu7mtzjOmcNXfQ==/109951163208857452.jpg"
            },{
                url: "http://p1.music.126.net/CzH0V_Do-9uBoZ6ZXk7alQ==/109951163208341646.jpg"
            }, {
                url: "http://p1.music.126.net/sz-L__kRDIK5TDelRy1Clw==/109951163208320270.jpg"
            }, {
                url: "http://p1.music.126.net/oShqLbK1hWHbcXCDykbJjg==/109951163106517017.jpg"
            },{
                url: "http://p1.music.126.net/GWQw6Z5ox8Fmal7hd_fy5w==/109951163208659609.jpg"
            }, {
                url: "http://p1.music.126.net/C_E9xkzwxfJHJrcIZ4PtVA==/109951163106930770.jpg"
            }]
        };
    },
    created() {
        this.$store.dispatch("GETALL")
    },
    computed: {
        album() {
            return this.$store.state.mapList.album
        },
        recommend() {
            return this.$store.state.mapList.recommend
        }
    },
    methods: {
        showAlbum(item, index) {
            this.$store.commit("SHOWORHIDEALBUM", {
                isShowAlbum: true,
                album: item,
                index: index
            });
        },
        playRecommend(recommend,index){
            this.$store.commit("PLAYAUDIO",{
                isShowPlayer : true,
                album:recommend,
                index:index,
                playerbg:this.recommend[index].playerbg,
                albumImage:this.recommend[index].albumImage,
                albumIndex : null
            })
        }
    },
    components: {
        VuiSwiperX,
    }
}

</script>
