<template>
<div class="moviebox" style="border-top: 0.5rem solid rgb(241 241 241 / 80%);">
	<div class="box_header">
		<span style="float: left;font-size: 0.9rem;margin-left: 0.7rem;"><i class="title_icon"></i>&nbsp;明星势力榜</span><span class="more">查看更多</span>
	</div>
	<v-touch class="content">
		<ul class="items">
			<li v-for="(list, index) in news" @click="Toshow(list)" :key="index">
				<div :style="{backgroundImage:`url(${list.coverurl})`}"><img v-if="index < 3" src="http://aladjs.cn/medals.png"/><span v-if="index < 3">{{list.dbscore}}</span><span v-else style="border-radius: 50%;color:black;background:white">{{list.dbscore}}</span></div>
				<span style="overflow: hidden;
text-overflow: ellipsis;
white-space: nowrap;">{{list.filmname}}</span>
			</li>
		</ul>
	</v-touch>
</div>
</template>
<script>
export default{
	data(){
		return{
			list:''
		}
	},
	name:'movieBox',
	props:["news"],
	methods:{
		Toshow:function(list){
			console.log(list)
			this.$router.push({path:`/show/${list._id}`});
		}
	}
}
</script>
<style lang="scss" scoped>
// $contentwidth
.moviebox{
	position: relative;
	width: 100%;
	height: 6.5rem;
	/*background: red;*/
/*	top:-1.5rem;*/
    margin-top: 0.5rem;
	border-top: 1px solid rgba(215,215,215,0.6);
}
.box_header{
	position: relative;
	top: 0px;
	/*background: black;*/
	height: 2rem;
	width: 100%；
}
.box_header span{
	/*background: red;*/
	position: relative;
	display: inline-block;
	width:25%;
	height: 2rem;
	line-height: 2rem;
}
.content{
	width: 100%;
	/*background: black;*/
	height: 5rem;
	overflow-x: auto;
    overflow-y: hidden;
    white-space: nowrap;
}
.content .items{
	width: calc(8rem*5 + 1rem);
	height: 100%;
	/*background: red;*/
}
.content .items li{
	width: 4rem;
	height: 4rem;
    border-radius: 50%;
	/*background: black;*/
	float: left;
	margin-left: 0.2rem;
}
.content .items li div{
	width: 80%;
	margin-left: 10%;
	margin-top: 10%;
	height: 80%;
    border-radius: 50%;
	/*background: yellow;*/
	background-size: 100% 100%;
	background-repeat: no-repeat;
	position: relative;
}
.content .items li div img{
	width: 1.2rem;
	height: 1.2rem;
	position: absolute;
	right: 0
}
.content .items li div span{
	width: 1.2rem;
	height: 1.2rem;
    line-height:1.8rem;
	position: absolute;
	right: 0;
	font-weight: 700
}
.content .items li span{
	position: relative;
	font-size: 0.7rem;
	/*background: black;*/
	display: block;
}
.more{
	float: right;
	font-size: 0.7rem
}
.title_icon{
    background: url(http://aladjs.cn/rank.png);
    width: 15px;
    height: 15px;
    background-repeat: no-repeat;
    display: inline-block;
    background-size: 100%;
    position: relative;
    top: 2px;
}
</style>