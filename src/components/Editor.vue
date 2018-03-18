<template>
	<div id="editor">
		<nav>
			<ol>
				<li 
				v-for = "i in [0,1,2,3,4,5]"
				v-bind:class = "{active:currentTab == i}"
				v-on:click = "currentTab = i"
				>
					<svg class="icon">
    					<use v-bind:xlink:href="`#icon-${icons[i]}`"></use>
					</svg>
				</li>				
			</ol>
		</nav>
		<ol class="panes">
			<li v-bind:class="{active:currentTab == 0}">
				<profileEditor v-bind:profile="resume.profile" />
			</li>
			<li v-bind:class="{active:currentTab == 1}">
				<workEditor v-bind:workHistory="resume.workHistory" />
			</li>
			<li v-bind:class="{active:currentTab == 2}">
				<StudyHistory v-bind:items="resume.items"></StudyHistory>
			</li>
			<li v-bind:class="{active:currentTab == 3}">
				<Reward v-bind:reward="resume.reward"></Reward>
			</li>
			<li v-bind:class="{active:currentTab == 4}">
				<Poject v-bind:poject="resume.poject"></Poject>
			</li>
			<li v-bind:class="{active:currentTab == 5}">
				<Telephone v-bind:telephone="resume.telephone"></Telephone>
			</li>
		</ol>
	</div>
</template>

<script>
	import ProfileEditor from './profileEditor'
	import WorkEditor from './workEditor'
	import StudyHistory from './studyHistoryEditor'
	import Reward from './RewardEditor'
	import Poject from './PojectEditor'
	import Telephone from './telephoneEditor'
	export default {
		props:['resume'],
		components:{
			ProfileEditor,
			WorkEditor,
			StudyHistory,
			Reward,
			Poject,
			Telephone
		},
		data(){
			return {
				currentTab:0,
				icons:['zheng','work','book','jiang','poject','telephone'],
			}
		},
		methods:{
			
		},
		created(){

		}
	}
</script>

<style lang="scss">
	#editor{
		text-align:center;
		min-height:80px;
		display: flex;
		> nav{
			background:#222;
			width:6em;
			border-radius:5px 0 0 5px;
		}
		nav > ol > li{
			cursor: pointer;
			padding:16px 0;
			 > .icon{
			 	fill: #fff;
			 }
			 &.active{
			 	background:#fff;
			 	>.icon{
			 		fill: #111;
			 	}
			 }
		}
		> .panes{
			overflow: auto;
			flex:1;
			>li{
				text-align: left;
				padding:24px;
				display:none;
				height:100%;
				overflow: auto;
			.wrap{
				margin:24px 0;
				padding:4px;
				position:relative;
				border-bottom:2px solid rgba(0,0,0,0.2);
				border-radius:5px;
				background:rgba(0,0,0,0.02);
				box-shadow:0 0 3px hsla(0,0,0,0.3);
				}
			.demonstration{
				display: block;
				padding-bottom:1em;
			}	
			.addbtn{
				display: block;
				margin:0 auto;
			}
			.colse{
				cursor: pointer;
				position: absolute;
				top:4px;
				right:4px;
				font-size:1.4em;
				color:rgba(0,0,0,0.3);
				&:hover{
					color:red;
				}
			}	
				&.active{
					display:block;
				}
			}
		}
	}
</style>