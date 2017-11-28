<template>
    <div class="index">
       <header-top></header-top>
       <banner></banner>
       <div class="contentOu">
       	    <contentUs></contentUs>
       </div>
        aiyayayaya
    </div>
</template>
<script>
import headerTop from "../components/header-top.vue"
import banner from "../components/banner.vue"
import contentUs from '../components/content.vue'
export default{
    components:{
        headerTop,
        banner,
        contentUs
    }
}

</script>
<style>
	.index{
		.contentOu{
			position: fixed;
			right: 30px;
			top: 550px;

		}
	}
</style>