<template>
	<div>
		<h2>获奖经历</h2>
		<el-form>
			<div class="wrap" v-for="(item,index) in reward">
				<el-form-item label="获奖名称">
					<el-input v-model="item.name" placeholder="获奖名称"></el-input>
					</el-form-item>
					<el-form-item label="获奖内容">
					<el-input
					  type="textarea"
					  :rows="6"
					  placeholder="请输入获奖内容"
					  v-model="item.content">
					</el-input>
					</el-form-item>
					<i class="el-icon-error colse" v-on:click="removeReward(index)"></i>
			</div>
			<el-button class="addbtn" type="primary" v-on:click="addReward">添加</el-button>	
		</el-form>
	</div>
</template>

<script>
	export default{
		props: ['reward'],
		methods:{
			addReward(){
				this.reward.push({
					name: '', content: ''
				})
			},
			removeReward(index){
				this.reward.splice(index,1)
			}
		}	
	}
</script>