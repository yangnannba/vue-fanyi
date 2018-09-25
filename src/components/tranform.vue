<template>
	<div class="container">
		  <div class="row">
				<div class="col-md-6 col-md-offset-3 well">
					<form v-on:submit="formsubmit" class="form-inline">
						
						<div class="form-group">
							<label class="sr-only" for="id">Email address</label>
											
							<input class="form-control" v-model="fanvalue" type="text" id="id" placeholder="请输入你要翻译的内容"/>
						</div>
						<div class="form-group">
							<label class="sr-only" for="id1">Email address</label>						
							<select class="form-control" id="id1" v-model="language">
								<option value="en">英语</option>
								<option value="fr">法文</option>
								<option value="ru">俄文</option>
								<option value="tr">土耳其</option>
							</select>
						</div>
						<button type="submit" class="btn btn-primary">确定</button>
					</form>
				</div>				
			</div>
	</div>

</template>

<script>
export default {
  name: 'tranform',
  data () {
    return {
       fanvalue:"",
			 language:"en"
    }
  },
	methods:{
		formsubmit:function(e){
			
			e.preventDefault();
			//alert(this.fanvalue);
			if(this.fanvalue){
				this.$emit("fuform",this.fanvalue,this.language)
			}
			
		}
	}
}
</script>


<style scoped>

</style>
