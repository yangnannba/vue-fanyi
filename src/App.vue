<template>
  <div id="app">
		<h1>翻译</h1>
		<h4 class="text-muted">简洁/方便/高效</h4>
		<tranform v-on:fuform="formsubmit" ></tranform>
		<jieguo :myvalue="value"></jieguo>
  </div>
</template>

<script>
import tranform from "./components/tranform"
import jieguo from "./components/jieguo"
export default {
  name: 'App',
	data(){
		return{
			value:""
		}
	},
	components:{
		tranform:tranform,
		jieguo:jieguo
	},
	methods:{
		formsubmit:function(e,lan){
			this.$http.get("https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20180827T025423Z.181fc5ea338c8eea.523323c29214ca9ea3e8fa4ec9b58115cf33977e&text="+e+"&lang="+lan)
    .then(function(res){
			//console.log(res.data.text[0]);
			this.value=res.data.text[0];
		})
		}
	}
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
