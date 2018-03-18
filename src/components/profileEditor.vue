<template>
	<div>
		<h2>个人信息</h2>
		<el-form class="wrap">
			<el-form-item label="姓 名">
				<el-input v-model="profile.name" placeholder="你的姓名"></el-input>
			</el-form-item>
			<el-form-item label="城 市">
				<el-input v-model="profile.city" placeholder="你所在的城市"></el-input>
			</el-form-item>
			<el-form-item label="性 别">
				<el-input v-model="profile.sex" placeholder="性别"></el-input>
			</el-form-item>
			<el-form-item label="年 龄">
				<el-input v-model="profile.age" placeholder="年龄"></el-input>
			</el-form-item>
			<span class="demonstration">出生年月</span>
				<el-date-picker
			      v-model="profile.birth"
			      type="date"
			      placeholder="选择日期"
			      format="yyyy 年 MM 月 dd 日"
			      value-format="yyyy-MM-dd">
			 </el-date-picker>
		</el-form>
	</div>
</template>

<script>
	export default {
		props: ['profile']
	}
</script>