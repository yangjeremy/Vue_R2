<template>
	<div id="preview">
		<section class="basicinfo">
			<h2>
				<span>
					<svg class="icon">
    					<use xlink:href="#icon-zheng"></use>
					</svg>
				</span>
			基本信息 | BASICINFO
				</h2>
			<p>姓名:{{resume.profile.name || '请填写名称'}}</p>
			<p>城市:{{resume.profile.city || '请填写城市'}}</p>
			<p>出生年月:{{resume.profile.birth || '请填写生日'}}</p>
			<p>性别:{{resume.profile.sex || '请填写性别'}}</p>
			<p>年龄:{{resume.profile.age || '请填写年龄'}}</p>
		</section>
		<section class="wrok" v-if="filter(resume.workHistory).length > 0">
			<h2>
				<span>
					<svg class="icon">
    					<use xlink:href="#icon-work"></use>
					</svg>
				</span>
				工作经历 | EXPERIENCE
			</h2>
			<ul>
				<li v-for="workHistory in filter(resume.workHistory)">
					<p>工作单位:{{workHistory.company}}</p>
					<p>工作时间:{{workHistory.time}}至{{workHistory.time2}}</p>
					<p>工作内容:{{workHistory.content}}</p>
				</li>
			</ul>
		</section>
		<section class="study" v-if="filter(resume.items).length > 0">
			<h2>
				<span>
					<svg class="icon">
    					<use xlink:href="#icon-book"></use>
					</svg>
				</span>
					学习经历 | EDUCATION
			</h2>
			<ul>
				<li v-for="items in filter(resume.items)">
					<p>学校:{{items.school}}</p>
					<p>学位:{{items.degree}}</p>
					<p>学习时间:{{items.duration}}至{{items.duration2}}</p>
				</li>
			</ul>
		</section>
		<section class="awards" v-if="filter(resume.reward).length > 0">
			<h2>
				<span>
					<svg class="icon">
    					<use xlink:href="#icon-jiang"></use>
					</svg>
				</span>
				获奖经历 | AWARDS
			</h2>
			<ul>
				<li v-for="reward in filter(resume.reward)">
					<p>奖项:{{reward.name}}</p>
					<p>获奖内容:{{reward.content}}</p>
				</li>
			</ul>
		</section>
		<section class="poject" v-if="filter(resume.poject).length > 0">
			<h2>
				<span>
					<svg class="icon">
    					<use xlink:href="#icon-poject"></use>
					</svg>
				</span>
				项目 | PROJECTS
			</h2>
			<ul>
				<li v-for="poject in filter(resume.poject)">
					<p>项目名称:{{poject.pojectName}}</p>
					<p>项目内容:{{poject.pojectContent}}</p>
				</li>
			</ul>
		</section>
		<section class="contacts">
			<h2>
				<span>
					<svg class="icon">
    					<use xlink:href="#icon-telephone"></use>
					</svg>
				</span>
				基本信息 | CONTACTS
			</h2>
			<p>电话:{{resume.telephone.number || '你的电话'}}</p>
			<p>微信:{{resume.telephone.weixin || '你的微信'}}</p>
			<p>QQ:{{resume.telephone.QQ || '你的QQ'}}</p>
			<p>github:{{resume.telephone.github || '你的github'}}</p>
		</section>
	</div>
</template>

<script>
	export default{
		props:['resume'],
		methods:{
			filter(arr){//找出非空对象 只要有一个value不是false 就返回 false
				return arr.filter(item=>!this.isEmpty(item))
			},
			isEmpty(obj){
				let empty = true
				for(let key in obj){
					if (obj[key]) {
						empty = false
						break
					}
				}
				return empty
			}
		}
	}
</script>

<style lang="scss">

	#preview{
		padding:24px;
		line-height:32px;
		overflow:auto;
		color:#017b51;
		> section{
			padding:8px;
			border-bottom:1px solid rgba(0,0,0,0.3);
			.icon{
				width:32px;
				height:32px;
				vertical-align: center;
			}
			> h2{
				display: inline-block;
				vertical-align: center;
				font-size:2em;
				padding:8px;
			}
			> p{
				font-size:1.25em;
				letter-spacing: 0.1em;
				color:#01517b;
			}
			> ul{
				font-size:1.25em;
				color:#01517b;
				> li{
					max-width:480px; 
					border-bottom:1px solid rgba(0,0,0,0.3);
					padding:8px 0 8px 0;
					&:last-child{
						border-bottom:0;
					}
				}
			}
		}
	}
</style>