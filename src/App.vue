<template>
  <div id="app" v-bind:class="{previewMode:previewMode}">
    <Topbar class="topbar" v-on:preview="preview" />

    <main>
      <Editor v-bind:resume="resume" class="editor" />
      <Preview v-bind:resume="resume" class="preview" />
    </main> 
      <el-button type="warning" id="out" v-on:click="out">退出</el-button>
  </div>
</template>


<script>
import Topbar from './components/Topbar'
import Editor from './components/Editor'
import Preview from './components/Preview'

export default {
  data(){
    return {
      previewMode:false,
      resume: {
        profile:{
          name:'',
          city:'',
          birth:'',
          sex:'',
          age:''
        },
        workHistory:[
          {company: '', time:'',time2:'',content: ''}
        ],
        items:[
          {school:'',duration:'',duration2:'',degree:''} 
        ],
        reward:[
          {name:'',content:''}
        ],
        poject:[
          {pojectName:'',pojectContent:''}
        ],
        telephone:[
          {number:'',weixin:'',QQ:'',github:''}
        ]
      }
    }
  },
  methods:{
    out(){
      this.previewMode = false
    },
    preview(){
      this.previewMode = true
    }
  },
  components:{
    Topbar,
    Editor,
    Preview
  }
}

</script>

<style lang="scss">
html,body{
  height:100%;
  overflow:hidden;
}
.icon {
   width: 3em; height: 3em;
   vertical-align: -0.15em;
   overflow: hidden;
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  height:100%;
  display: flex;
  flex-direction: column;
}
.topbar{
  position:relative;
  z-index:1;
  box-shadow:inset 0 0 3px;
}

#app main{
  display:flex;
  flex:1;
  animation:5s change linear infinite;
  > .editor{
    background:#fff;
    width:43em;
    margin:16px 8px 16px 16px;
    box-shadow:0 0 3px hsla(0,0,0,0.5);
    border-radius:5px;
  }
  > .preview{
     background:#fff;
    flex:1;
    box-shadow:0 0 3px hsla(0,0,0,0.5);
    border-radius:5px;
  }
}
@keyframes change{
  0%,
  80%,
  100%{
    background:#00264a;
  }
  10%{
    background:#05529b;
  }
}

.preview{
  margin:16px 16px 16px 8px;
}

.previewMode > #topbar{
   display:none;
}

.previewMode #editor{
   display:none;
}

.previewMode #preview{
   max-width: 1080px;
   margin: 16px auto;
}

#out{
  display:none;
}

.previewMode #out{
  display: inline-block;
  position:fixed;
  right:24px;
  top:16px;
}

</style>
