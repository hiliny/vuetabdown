<template>
	<div class="tab-down">
		<input type="text" @keyup="keyupHandle" v-model="valz" @click="clickInput">
		<ul :style="{display:showPull?'':'none'}">
			<li>可输入名称或检索码</li>
			<li v-for="(a,index) in list" @click="itemClick($event,a)">{{a.name}}</li>
		</ul>
	</div>
</template>
<script>
	export default {
		name:"ElPulldown",
		props:{
			list:{
				type:Array,
				require:true
			}
		},
		data:function(){
			return {
				valz:"",
				showPull:false
			};
		},
		computed:{
		},
		mounted:function(){
			var _this= this;
		},
		methods:{
			keyupHandle:function(){
				this.showPull = true;
			},
			itemClick:function(ev,data){
				this.valz = data.name;
				this.showPull = false;
			},
			clickInput:function(){
				this.showPull = true;
			},
			blurHandle:function(){
				var _this = this;
				_this.showPull = false;	
			}
		}
	}
</script>
<style scoped>
	.tab-down{
		position: relative;
		display: inline-block;
	}
	.tab-down ul{
		padding: 0;
		margin: 0;
		position: absolute;
		left: 0;
		border: 1px solid #ddd;
		width: 100%;
		box-sizing: border-box;
		z-index: 999;
	}
	.tab-down ul li{
		padding: 3px 5px;
		cursor: pointer;
		display: list-item;
		margin: 0px;
		border-bottom: 1px solid #ddd;
		text-align: left;
		line-height: 20px;
	}	
	.tab-down ul li:hover,.tab-down ul li:hover{
		background-color: #5FB878;
		color: #fff;
	}
</style>