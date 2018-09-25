<template>
  <div class="users">
		  <input v-model="newuser.name" />
		  <input v-model="newuser.email" />
			<button v-on:click="queding">确定</button>
      <ul>
				<li v-for="(user,index) in users"><input type="checkbox" v-model="user.myshow" /><span :class="{under:user.myshow}">{{user.name}}:{{user.email}}</span><button v-on:click="shan(index)">x</button></li>
			</ul>
  </div>
</template>

<script>
export default {
  name: 'users',
  data () {
    return {
			 newuser:{},
       users:[
				 {name:"name1",email:"52900@qq.com",myshow:false},
				 {name:"name2",email:"52900@qq.com",myshow:false},
				 {name:"name3",email:"52900@qq.com",myshow:false}
			 ]
    }
  },
	methods:{
		queding:function(){
			this.users.push({
				name:this.newuser.name,
				email:this.newuser.email,		
				myshow:false
			})
		},
		shan:function(e){
			  this.users.splice(e,1)
		}
	},
	created:function(){
		this.$http.get("http://jsonplaceholder.typicode.com/users")
		.then(function(res){
			 //console.log(res.data)
       this.users=res.data

		})
	}
}
</script>


<style scoped>
ul{
	list-style:none;
}
.under{
	text-decoration: line-through;
}
</style>
