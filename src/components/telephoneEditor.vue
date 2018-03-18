<template>
	<div>
		<h2>联系方式</h2>
		<el-form>
			<el-form-item label="电话">
				<el-input v-model="telephone.number" placeholder="number"></el-input>
			</el-form-item>

			<el-form-item label="微信">
				<el-input v-model="telephone.weixin" placeholder="weixin"></el-input>
			</el-form-item>

			<el-form-item label="QQ">
				<el-input v-model="telephone.QQ" placeholder="QQ"></el-input>
			</el-form-item>

			<el-form-item label="github">
				<el-input v-model="telephone.github" placeholder="github"></el-input>
			</el-form-item>
					
		</el-form>
	</div>
</template>

<script>
	export default {
		props: ['telephone']
	}
</script>