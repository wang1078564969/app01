<template>
	<div class="user">
		<h2>用户管理 {{msg}}</h2>
	
		<div class="btns">
			<button>添加</button>
		</div>
		<table class="table">
			<thead>
				<tr>
					<th>编号</th>
					<th>姓名</th>
					<th>性别</th>
					<th>生日</th>
					<th>入职时间</th>
					<th>身份</th>
					<th>操作</th>
				</tr>
			</thead>
			<tbody>
				<tr v-for='user in users'>
					<td>
						<input type="checkbox">
					</td>
					<td>{{user.name}}</td>
					<td>{{user.gender}}</td>
					<td>{{user.birth}}</td>
					<td>{{user.hiredate}}</td>
					<td>{{user.type}}</td>
					<td>
						<a href="javascript:void(0);" v-on:click="delect(user.id)">删除{{user.id}}</a>
						<a href="javascript:void(0);">修改</a>
					</td>
				</tr>
			</tbody>
		</table>
	</div>
</template>
<script>
	import {baseUrl} from '@/config/url'
	export default {
		data(){
			return {
				msg:'hello',
				users:[]
			}
		},
		methods:{
			deleteUserById(id){
				alert(id);
			},
			delect(id){
				console.log(id);
				$.get(baseUrl+"/user/deleteById",{id:id},({stauts})=>{
					console.log(stauts);
				})
			},
			loadUsers(ls){
				$.get(baseUrl+"/user/findAll",({stauts,data})=>{
					if(stauts == 200){
						ls(data);
						console.log(data);
							
					} else {
						alert('加载失败');
					}
				})
			}
			// loadUsers(ls){
			// 	$.get(baseUrl+"/user/findAll",({stauts,data})=>{
			// 		if(stauts == 200){
			// 			ls(data);
			// 		} else {
			// 			alert('加载失败');
			// 		}
			// 	})
			// }
		},
		beforeMount(){
			this.loadUsers((data)=>{
				this.users = data;
			})
		}
		
	}
</script>

<style>
	.btns {
		margin: .5em 0;
	}
	.table {
		width: 90%;
		border-collapse: collapse;
	}
	.table td, .table th {
		border:1px solid #ededed;
		line-height: 1.6em;
	}

</style>
 