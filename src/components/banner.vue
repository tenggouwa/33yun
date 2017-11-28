<template>
    <div class="banner">
        <div class="contaner">
        	<el-carousel height="420px">
			    <el-carousel-item v-for="item in dataList" :key="item">
			        <div class="bannerL">
			        	<h3>{{item.name}}</h3>
				        <p>{{item.info}}</p>
				        <button>{{item.inni}}</button>
			        </div>
			    </el-carousel-item>
			</el-carousel>
        </div>	
        <div class="contaner-bottom">
        	<div class="fivePoint">
        		<div>
        			<i class="iconfont icon-diqiu"></i>
        			<p>网络增强云服务器</p>
        			<span>450万PPS,稳定低延迟</span>	
        		</div>
        		<div>
        			<i class="iconfont icon-diqiu"></i>
        			<p>网络增强云服务器</p>
        			<span>450万PPS,稳定低延迟</span>	
        		</div>
        		<div>
        			<i class="iconfont icon-diqiu"></i>
        			<p>网络增强云服务器</p>
        			<span>450万PPS,稳定低延迟</span>	
        		</div>
        		<div>
        			<i class="iconfont icon-diqiu"></i>
        			<p>网络增强云服务器</p>
        			<span>450万PPS,稳定低延迟</span>	
        		</div>
        		<div class="last-border">
        			<i class="iconfont icon-diqiu"></i>
        			<p>网络增强云服务器</p>
        			<span>450万PPS,稳定低延迟</span>	
        		</div>
        	</div>
        </div>
    </div>
</template>
<script>
export default{
	data(){
		return{
			dataList:[],
		}		
	},
	mounted(){
		this.dataList=[{
		    "name": "第四代云服务器 全新上线",
		    "info": "十倍性能提升，多场景规格足，打造最佳性价比选择",
		    "inni": "查看详情",
		    
		},{
		    "name": "聚焦智能制造、企业数字化转型",
		    "info": "2017云栖大会|苏州峰会 火热报名中",
		    "inni": "立即报名",
		    
		},{
		    "name": "云数据库Redis单点集群上线",
		    "info": "超凡性价比，满足百万QPS，针对超大型纯缓存业务定制",
		    "inni": "查看详情",
		    
		},{
		    "name": "竞价型GPU云服务器实例",
		    "info": "低至一折起，大幅度降低GPU成本",
		    "inni": "查看详情",
		    
		},{
		    "name": "应用配置管理ACM全新上线",
		    "info": "了解如何极大程度减轻配置管理工作量",
		    "inni": "查看详情",
		    
		}]
	},
	methods:{
	}
}
</script>
<style>
	.banner{
		width: 100%;
		height: 540px;
		background:linear-gradient(#182762,#116f98);
		.contaner{
			width: 1200px;
			margin: 0 auto;
			height: 440px;
			color: #fff;
			.bannerL{
				text-align: left;
				padding-left: 80px;
				h3{
					margin-top: 80px;
					font-size: 46px;
				}
				p{
					font-size: 20px;
				}
				button{
					width: 120px;
					height: 35px;
					border: 1px solid #fff;
					background: none;
					color: #fff;
					font-size: 16px;
					border-radius: 0;
					cursor: pointer;
					margin-top: 40px;
					transition: all 0.3s ease 0s;
                    -moz-transition: all 0.3s ease 0s;
                    -webkit-transition: all 0.3s ease 0s;
                    -o-transition: all 0.3s ease 0s;
				}
				button:hover{
					color: #000;
					background: #fff;
				}
			}
		}
		.contaner-bottom{
			width: 100%;
			height: 100px;
			background: rgba(106,161,210,0.4);
			.fivePoint{
				width: 1200px;
				height: 100px;
				margin: 0 auto;
				div{
					float: left;
					width: 240px;
					height: 100px;
					border-left: 1px solid #348aab;
					text-align: left;
					cursor: pointer;
					transition: all 0.3s ease 0s;
					-moz-transition: all 0.3s ease 0s;
					-webkit-transition: all 0.3s ease 0s;
					i{
						float: left;
						font-size: 40px;
						color: #fff;
						line-height: 100px;
						margin-left: 15px;
						margin-right: 10px;
					}
					p{
						color: #fff;
						font-size: 16px;
						font-weight: bold;
						margin-top: 28px;
					}
					span{
						color: #fff;
						font-size: 14px;
					}
				}
				div:hover{
					background: none repeat scroll 0 0 #3488a9;
				}
				.last-border{
					border-right: 1px solid #348aab;
				}
			}
		}
	}
</style>