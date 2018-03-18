<template>
	<div>
		<h2>学习经历</h2>
		<el-form>
			<div class="wrap" v-for="(item,index) in items">
				<el-form-item label="学 校">
					<el-input v-model="item.school" placeholder="请输入学校名称">					
					</el-input>
				</el-form-item>
				<el-form-item label="学位">
					<el-input v-model="item.degree" placeholder="请输入学位">					
					</el-input>
				</el-form-item>
				<!-- item.duration -->
				<span class="demonstration">学习时间</span>
				<el-date-picker
			      v-model="item.duration"
			      type="date"
			      placeholder="选择日期"
			      format="yyyy 年 MM 月 dd 日"
			      value-format="yyyy-MM-dd">
			    </el-date-picker>
			    至
			    <el-date-picker
			      v-model="item.duration2"
			      type="date"
			      placeholder="选择日期"
			      format="yyyy 年 MM 月 dd 日"
			      value-format="yyyy-MM-dd">
			    </el-date-picker>

				<i class="el-icon-error colse" v-on:click="removeItem(index)"></i>
			</div>
			<el-button class="addbtn" type="primary" v-on:click="addItem">添加</el-button>	
		</el-form>
	</div>
</template>

<script>
	export default{
		props: ['items'],
		methods:{
			addItem(){
				this.items.push({
					school: '', degree: '',duration:''
				})
			},
			removeItem(index){
				this.items.splice(index,1)
			}
		}	
	}
</script>