<template>
    <div class="header">
        <div class="headerTop-headerCenter">
            <div class="header-top">
            <!-- 阿里云图标 -->
                <div class="icon">
                    <i class="iconfont icon-aliyun01"></i>
                </div>
                <div class="tab-icon">
                    <div class="name">
                        <!-- 搜索 -->
                        <span class="find">
                            <i class="iconfont icon-sousuo" v-if="show1" @click="sendtheinput"></i>
                            <transition name="el-zoom-in-center">
                                <el-input
                                class="nameclass"
                                    v-if="!show1"
                                    :focus="haha"
                                    @blur="chekcheck"
                                    size="mini"
                                    placeholder="请输入内容"
                                    prefix-icon="el-icon-search"
                                    v-model="input21">
                                </el-input>
                            </transition>
                        </span>
                        <span class="international" 
                            @mouseover="intershow=false" 
                            @mouseout="intershow=true"
                            :class="{colorback:intershow==false}">
                            <i class="iconfont icon-diqiu"></i>
                            <span>{{internalNow}}</span>
                            <i v-show="intershow" class="el-icon-arrow-down"></i>
                            <i v-show="!intershow" class="el-icon-arrow-up"></i>   
                        </span>
                        <!-- 语言选择 -->
                        <div class="intertab" v-show="!intershow" @mouseout="intershow=true" @mouseover="intershow=false">
                            <ul>
                                <li v-for="item in interList" @click="jumpInternal(item)">{{item}}</li>
                            </ul>
                        </div>
                    </div>
                    <div class="tabclass">
                        <ul>
                            <li v-for="item in ulList">{{item}}</li>
                        </ul>
                    </div>
                </div>
            </div>
            <div class="header-center">
                <div class="all-tab" @mouseover="overThetab" @mouseout="outThetab" :class="{titl:tabtitl == true}">
                    <i class="iconfont icon-menu"></i>
                    <span>全部导航</span>
                </div>
                <div class="other-tab">
                    <ul>
                        <li v-for="(item,key) in tabsname" 
                            @mouseover="toptabover(key)" 
                            @mouseout="toptabout"
                            :class="{keyboard:toptabkey==key,keyboard1:toptabkey==-1}"
                            >{{item}}</li>
                    </ul>
                </div>
                <div class="tab-btn">
                    <button>免费注册</button>
                </div>
            </div>
            <div class="header-left" id="headerLeft" @mouseover="overThetab" @mouseout="outThetab">
                <ul>
                    <li v-for="(item,key) in tabList" 
                        @mouseover="childover(key)" 
                        @mouseout="childout()"
                        :class="{fontcolor:onToSecond == key}">
                        <span>{{item}}</span>
                        <i class="el-icon-arrow-right"></i>
                    </li>
                    <li class="jiangyou"></li>
                </ul>
            </div>
            <div class="header-leftSecond" id="LeftSecond" @mouseover="childover(onToSecond)" @mouseout="childout()">
                <ul>
                    <li v-for="item in secondtabList">
                        <span>{{item}}</span>
                    </li>
                    <li class="jiangyousecond"></li>
                </ul>
            </div> 
            <div class="header-topSecond" 
                @mouseover="toptabover(toptabkey)" 
                @mouseout="toptabout()">
                <el-collapse-transition>
                    <div class="ulNext" v-show="show3" @mouseover="checkover" @mouseout="chekout()">
                        <ul v-for="item in bigList">
                            <li>{{item}}</li>
                        </ul>
                    </div>
                </el-collapse-transition>
            </div>  
        </div>
    </div>
</template>
<script>
export default{
    data(){
        return{
            input21:'',
            haha:true,
            show1:true,
            show3:false,
            intershow:true,
            allbackshow:false,
            tabtitl:false,
            onToSecond:-1,
            toptabkey:-1,
            toptabkeys:'',
            internalNow:'中国站',
            ulList:['控制台','文档','备案','邮箱','登录'],
            interList:['中国站','International - English','International - 简体中文','日本呀咩爹'],
            tabsname:['最新活动','产品','解决方案','数据·智能','安全','云市场','支持','合作伙伴'],
            tabList:['产品','解决方案','云市场','合作与生态','云栖社区','阿里云大学','创业孵化','支持','开发者中心','了解阿里云','重要频道'],
            secondtabList:[],
            bigList:[],
        }
    },
    mounted(){
        this.getHeight();
    },
    methods:{
        //获取菜单高度
        getHeight(){
            let e = window.screen.availHeight-100;
            document.getElementById('headerLeft').style.height = e+'px';
            document.getElementById('LeftSecond').style.height = e+'px';
        },
        jumpInternal(e){
            this.internalNow = e;
        },
        // 一级菜单显示
        overThetab(){
            this.tabtitl = true;
            let e = 0 + 'px';
            document.getElementById('headerLeft').style.left = e;
        },
        // 一级菜单隐藏
        outThetab(){
            this.tabtitl = false;
            let e = -200 + 'px';
            document.getElementById('headerLeft').style.left = e;
        },
        // 二级菜单显示
        childover(a){
            this.overThetab();
            this.onToSecond = a;
            let e = 200 + 'px';
            document.getElementById('LeftSecond').style.left = e;
            if(a == 0){
                this.secondtabList=['弹性计算','储存和CDN','数据库','网络','域名与网站','安全'];
            }else if(a == 1){
                this.secondtabList=['行业解决方案','通用解决方案','安全解决方案','大数据解决方案','DevOps解决方案'];
            }else if(a == 2){
                this.secondtabList=['基础软件市场','网站建设','企业应用','服务与培训','安全市场'];
            }else if(a == 3){
                this.secondtabList=['加入合作伙伴','加入阿里云推广大使','加入阿里云CPS推广','蚂蚁金服开放合作','数梦工厂合作'];
            }else if(a == 4){
                this.secondtabList=['个人博客','团队博客'];
            }else if(a == 5){
                this.secondtabList=['基础软件市场','网站建设','企业应用','服务与培训','安全市场'];
            }else if(a == 6){
                this.secondtabList=['个人博客','团队博客'];
            }else if(a == 7){
                this.secondtabList=['基础软件市场','网站建设','企业应用','服务与培训','安全市场'];
            }else if(a == 8){
                this.secondtabList=['个人博客','团队博客'];
            }else if(a == 9){
                this.secondtabList=['基础软件市场','网站建设','企业应用','服务与培训','安全市场'];
            }else if(a == 10){
                this.secondtabList=['个人博客','团队博客'];
            }
        },
        // 二级菜单隐藏
        childout(a){
            this.outThetab();
            let e = -300 + 'px';
            document.getElementById('LeftSecond').style.left = e;
        },
        //头部菜单显示
        toptabover(e){
            this.toptabkey = e;
            this.toptabkeys = e;
            this.show3 = true;
            if(e == 0){
                this.bigList = ['加入合作伙伴','加入阿里云推广大使','加入阿里云CPS推广','蚂蚁金服开放合作','数梦工厂合作'];
            }else if(e == 1){
                this.bigList = ['加入合作伙伴','加入阿里云推广大使','加入阿里云CPS推广','蚂蚁金服开放合作'];
            }else if(e == 2){
                this.bigList = ['加入合作伙伴','加入阿里云推广大使','加入阿里云CPS推广'];   
            }else if(e == 3){
                this.bigList = ['加入合作伙伴','加入阿里云推广大使'];   
            }else if(e == 4){
                this.bigList = ['加入合作伙伴'];   
            }else if(e == 5){
                this.bigList = ['加入合作伙伴','加入阿里云推广大使'];   
            }else if(e == 6){
                this.bigList = ['加入合作伙伴','加入阿里云推广大使','加入阿里云CPS推广'];   
            }else if(e == 7){
                this.bigList = ['加入合作伙伴','加入阿里云推广大使','加入阿里云CPS推广','蚂蚁金服开放合作'];   
            }
        },
        //头部菜单隐藏
        toptabout(){
            this.show3 = false;
        },
        //控制上下对应
        checkover(){
            this.toptabkey = this.toptabkeys;
        },
        chekout(){
            this.toptabkey = -1;
        },
        sendtheinput(){
            this.show1 = false;
            console.log(this.show1)
        },
        chekcheck(){
            this.show1 = true;
            console.log(this.show1)
        }
    }
}
</script>
<style>
.header{
    .headerTop-headerCenter:hover .header-top{
        background: none repeat scroll 0 0 #373d41;
        border-bottom: 1px solid #555a5d;
        /*background: #373d41;*/
    }
    .headerTop-headerCenter:hover .header-center{
        background: none repeat scroll 0 0 #373d41;
        /*background: #373d41;*/
    }
    .headerTop-headerCenter{
        
        .header-top{
            transition: all 0.3s ease 0s;
            -moz-transition: all 0.3s ease 0s;
            -webkit-transition: all 0.3s ease 0s;
            -o-transition: all 0.3s ease 0s;
            background: #1a1958;
            color: #fff;
            height:40px;
            width:100%;
            border-bottom:1px solid #3b3d72;
            .icon{
                float: left;
                margin-left: 20px;
                line-height: 40px;
                i{
                    font-size: 25px;
                }
            }
            .tab-icon{
                float: right;
                line-height: 40px;
                height: 40px;
                .name{
                    float: left;
                    height: 40px;
                    .find{
                        float: left;
                        margin-right: 15px;
                        i{
                            font-size: 20px;
                            float: left;
                        }
                        .nameclass{
                            width:180px;
                            input{
                                background: #4f5356;
                                border: none;
                                color: #fff;
                            }
                           
                        }
                    }
                    .intertab{
                        z-index: 800;
                        position: fixed;
                        width: 200px;
                        /*height: 120px;*/
                        margin: -17px 0 0 35px;
                        background: #272b2f;
                        padding: 10px 15px;
                        ul{
                            text-align: left;
                            li{
                                line-height: 25px;
                                font-size: 14px;
                                cursor: pointer;
                            }
                        }
                    }
                    .colorback{
                        background: #272b2f;
                    }
                    .international{
                        display: inline-block;
                        height: 40px;
                        i{
                            margin:0 5px;
                            font-size: 20px;
                            font-weight: bold;
                            float: left;
                            line-height: 40px;
                        }
                        span{
                            display: inline-block;
                            font-size: 14px;
                            font-weight: bold;
                            height: 40px;
                            float: left;
                            line-height: 40px;
                            cursor: pointer;
                        }
                        ul{
                            float: right;
                            overflow: hidden;
                            li{
                                float: right;
                                width: 80px;
                                cursor: pointer;
                            }
                        }
                    }
                }
                .tabclass{
                    float: left;
                    ul{
                        li{
                            float: left;
                            width: 50px;
                            font-size:14px;
                            font-weight: bold; 
                            cursor: pointer;
                        }
                    }
                } 
            }
        }
        .header-center{
            transition: all 0.3s ease 0s;
            -moz-transition: all 0.3s ease 0s;
            -webkit-transition: all 0.3s ease 0s;
            -o-transition: all 0.3s ease 0s;
            width: 100%;
            height: 60px;
            background: #19225e;
            border-bottom: 1px solid #3b3d72;
            text-align: left;
            .all-tab{
                padding: 0 20px;
                margin-left: -105px;
                float: left;
                height: 60px;
                line-height: 60px;
                cursor: pointer;
                i{
                    color: #fff;
                    margin-right: 8px;
                    float: left;
                }
                span{
                    color: #fff;
                    font-size: 14px;
                    font-weight: bold;
                    display: inline-block;
                }
            }
            .titl{
                background: #00c1de;
            }
            .all-tab:hover{
                background: #00c1de;
            }
            .other-tab{
                float: left;
                margin-left: 20px;
                ul{
                    li{
                        float: left;
                        color: #fff;
                        font-size: 14px;
                        font-weight: bold;
                        line-height: 57px;
                        padding: 0 15px;
                        cursor: pointer;
                        transition: all 0.3s ease 0s;
                        -moz-transition: all 0.3s ease 0s;
                        -webkit-transition: all 0.3s ease 0s;
                        -o-transition: all 0.3s ease 0s;
                    }
                    .keyboard{
                        border-bottom: 2px solid #00c1de;
                        color: #00c1de;
                    }
                    .keyboard1{
                        color: #fff;
                        border-bottom: none;
                    }
                }
            }
            .tab-btn{
                float: right;
                margin-top: -1px;
                button{
                    width: 120px;
                    height: 61px;
                    border: none;
                    background: #00c1de;
                    color: #fff;
                    border-radius: 0;
                    font-size: 14px;
                    font-weight: bold;
                    cursor: pointer;
                }
            }
        }
        .header-left{
            z-index: 99;
            left: -200px;
            position: fixed;
            width: 200px;
            background: #272b2e;
            color: #fff;
            border-right: 1px solid #525558;
            margin-top: -1px;
            transition:left 0.5s;
            -moz-transition:left 0.5s; /* Firefox 4 */
            -webkit-transition:left 0.5s; /* Safari and Chrome */
            -o-transition:left 0.5s; /* Opera */
            ul{
                padding-top: 15px;
                .jiangyou{
                    width: 80%;
                    border-bottom: 1px solid #525558;
                    margin: 0 auto;
                }
                .fontcolor{
                    span{
                        color: #00c1de;
                    }
                    i{
                        color: #00c1de;
                    }
                }
                li{
                    padding: 0 20px;
                    line-height: 35px;
                    font-size: 14px;
                    font-weight: bold;
                    overflow: hidden;
                    cursor: pointer;
                    span{
                        float: left;
                        transition: all 0.3s ease 0s;
                        -moz-transition: all 0.3s ease 0s;
                        -webkit-transition: all 0.3s ease 0s;
                        -o-transition: all 0.3s ease 0s;
                    }
                    i{
                        float: right;
                        font-weight: bold;
                        margin-top: 10px;
                        color: #fff;
                        transition: all 0.3s ease 0s;
                        -moz-transition: all 0.3s ease 0s;
                        -webkit-transition: all 0.3s ease 0s;
                        -o-transition: all 0.3s ease 0s;
                    }
                }
                li:hover span{
                    color: #00c1de;
                }
                li:hover i{
                    color: #00c1de;
                }
            }
        }
        .header-leftSecond{
            z-index: 98;
            left: -300px;
            position: fixed;
            width: 300px;
            background: #303538;
            color: #fff;
            margin-top: -1px;
            transition:left 0.5s;
            -moz-transition:left 0.5s; /* Firefox 4 */
            -webkit-transition:left 0.5s; /* Safari and Chrome */
            -o-transition:left 0.5s; /* Opera */
            ul{
                padding-top: 15px;
                .jiangyousecond{
                    width: 85%;
                    border-bottom: 1px solid #525558;
                    margin: 0 auto;
                }
                li{
                    text-align: left;
                    padding: 0 20px;
                    line-height: 35px;
                    font-size: 14px;
                    font-weight: bold;
                    overflow: hidden;
                    cursor: pointer;
                    span{
                        float: left;
                        transition: all 0.3s ease 0s;
                        -moz-transition: all 0.3s ease 0s;
                        -webkit-transition: all 0.3s ease 0s;
                        -o-transition: all 0.3s ease 0s;
                    }
                }
                li:hover span{
                    color: #00c1de;
                }
            }
        }
        .header-topSecond{
            z-index: 97;
            margin-top: -1px;
            width: 100%;
            position: fixed;
            background: #272b2e;
            padding: 0 0 0 156px;
            text-align: left;
            color: #e5e5e5;
            font-weight: bold;
            font-size: 14px;
            transition: all 0.3s ease 0s;
            -moz-transition: all 0.3s ease 0s;
            -webkit-transition: all 0.3s ease 0s;
            -o-transition: all 0.3s ease 0s;
            .ulNext{
                ul{
                    float: left;
                    margin: 30px 30px 30px 0;
                    width: 180px;
                    li{
                        line-height: 24px;
                        cursor: pointer;
                    }
                    li:hover{
                        color: #00c1de;
                    }
                    li:first-child{
                        font-size: 16px;
                        color: #fff; 
                        padding-bottom: 10px;
                    }
                }
            }
        }
    }
}
</style>