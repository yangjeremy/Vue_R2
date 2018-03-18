<template>
	<div>
		<h2>项目</h2>
		<el-form>
			<div class="wrap" v-for="(item,index) in poject">
				<el-form-item label="项目名称">
					<el-input v-model="item.pojectName" placeholder="项目名称"></el-input>
					</el-form-item>
					<el-form-item label="项目内容">
					<el-input
					  type="textarea"
					  :rows="6"
					  placeholder="你的技术栈"
					  v-model="item.pojectContent">
					</el-input>
					</el-form-item>
					<i class="el-icon-error colse" v-on:click="removepoject(index)"></i>
			</div>
			<el-button class="addbtn" type="primary" v-on:click="addpoject">添加</el-button>	
		</el-form>
	</div>
</template>

<script>
	export default{
		props: ['poject'],
		methods:{
			addpoject(){
				this.poject.push({
					pojectName: '', pojectContent: ''
				})
			},
			removepoject(index){
				this.poject.splice(index,1)
			}
		}	
	}
</script>