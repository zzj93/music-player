<style scoped lang='stylus'>
	.banner{
		.img{
			width:100%;
		}
	}
	.title{
		position: relative;
		width: 100%;
		text-align: center;
		background-color:url(http://music.163.com/m/at/59c325d8e720bc24a700960f);
	
		.f-fs20{
			color:#333;
			font-size: 20px;
		}
		.s-fc5{
			line-height: 21px;
			color: #999;
			font-size: 14px;
		}
	}
	
</style>
<template>
	<div>
		<swiper >
        	<swiper-slide v-for="item in imgArr" :key="item.id" class="banner">
        	    <img :src="item.url" alt=""  class="img">
        	</swiper-slide>
    	</swiper>
    	<div class="title">
    		<h1 class="f-fs20 ">
				<span>音乐力量</span>
			</h1>
    		<h2 class="s-fc5 ">汇集全球优质音乐装备</h2>
    		<h3>还未搭建，敬请期待……</h3>
    	</div>
	</div>

</template>
<script>
export default {
    data() {
        return {
            imgArr: [
            	{
            	    url: "http://p3.music.126.net/t2gNYOweaQrq88w14Perrw==/109951163208421575.jpg" 
            	}
            ]
        };
    }
}
</script>