<template>
	<div class="contentUs">
		<div class="little" @mouseover="show = true" @mouseout="show = false">
			<i class="iconfont icon-zixun"></i><br>
			<span>咨<br>	询<br>&<br>建<br>议</span>
		</div>
		<transition name="el-fade-in-linear">
		<div class="contentinfor" v-show="show" @mouseover="show = true" @mouseout="show = false">
			<i class="el-icon-close name" @click="show=false"></i>
			<div class="contentme">
				<i class="iconfont icon-diqiu"></i>
				<p>售前咨询电话</p>
				<span>95187转1</span>
			</div>
			<div class="contentme">
				<i class="iconfont icon-diqiu"></i>
				<p>售前咨询电话</p>
				<span>95187转1</span>
			</div>
			<div class="contentme">
				<i class="iconfont icon-diqiu"></i>
				<p>售前咨询电话</p>
				<span>95187转1</span>
			</div>
		</div>
	</transition>
	</div>
</template>
<script>
	export default{
		data(){
			return{
				show:false,
			}
		},
		methods:{

		}
	}
</script>
<style>
	.contentUs{

		.little{
			width: 45px;
			height: 140px;
			background: #33cde5;
			box-shadow: 1px 1px 10px #a0a2a3;
			padding-top: 8px;
			i{
				color: #fff;
				font-size: 26px;
				font-weight: bold;
			}
			span{
				color: #fff;
				font-size: 14px;
				font-weight: bold;
			}
		}
		.contentinfor{
			width: 300px;
			height: 200px;
			background: #fff;
			position: fixed;
			right: 78px;
			top: 490px;
			box-shadow: 1px 1px 10px #a0a2a3;
			text-align: left;
			padding-left: 10px;
			.name{
				color: #666;
				font-size: 20px;
				float: right;
				margin: 10px 10px 0 0;
				cursor: pointer;
			}
			.contentme{
				i{
					font-size: 28px;
					float: left;
					margin: 0 10px;
				}
				p{
					margin-top: 25px;
					font-size: 14px;
				}
				span{
					color: #666;
				}
			}
		}
	}
</style>