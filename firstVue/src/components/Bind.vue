<template>
	<div class="bind">
		<div v-if="!user">
			<a href="javascript:void(0);" v-on:click='login'>登录</a>
		</div>
		<div v-else>
			欢迎您，{{user.name}}
		</div>
		<h1 v-on:click='foo'>{{a}}</h1>

		<form action="javascript:void(0)">
			<input type="text" v-model='name'>
			<input type="submit" value="保存" v-on:click='save'>
		</form>
		

		<ul>
			<li v-for='b in bs'>{{b.name}}</li>
		</ul>
	</div>
</template>
<script>
	export default {
		name:'bind',
		data(){
			return {
				name:'',
				a:'hello bind',
				bs:[{
					id:1,
					name:'terry'
				},{
					id:2,
					name:'larry'
				},{
					id:3,
					name:'tom'
				}],
				user:null
			}
		},
		methods:{
			foo(){
				console.log('foo',this);
				alert('hello');
			},
			login(){
				//将BS中第一个对象赋值给user
				this.user = this.bs[0];
			},
			save(){
				let user = {}
				user.id = this.bs.length+1;
				user.name = this.name;	
				this.bs.push(user);			
			}
		}
	}
</script>
<style>

</style>