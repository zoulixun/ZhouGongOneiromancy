<template>
	<div>
		<!-- <h1>MyDream</h1> -->
		<div class="row">
			<div class="col-md-6 col-md-offset-3">
				<form class="well form-inline" v-on:submit="formSubmit">
					<input v-model="dream" class="form-control" type="text" placeholder="输入你的梦,例如   '杀人了'">
					<input class="form-control btn btn-warning btn-circle btn-lg" type="submit" value="解">
				</form>
			</div>
			
			
		</div>
	
	</div>
</template>

<script>
	export default{
		name:'MyDream',
		data(){
			return{
				dream:""
			}
		},
		methods:{
			formSubmit(e){
				this.$emit("formSubmit",this.dream);
				e.preventDefault();
			}
		}
	}

</script>

<style scoped>
.form-control{
	border: none;
	outline: none;
	box-shadow: none;
	border-bottom: 1px solid #ced4da;
}
.btn:focus{
	outline: none;
}
.btn-circle {
  width: 30px;
  height: 30px;
  text-align: center;
  padding: 6px 0;
  font-size: 12px;
  line-height: 1.428571429;
  border-radius: 15px;
}
.btn-circle.btn-lg {
  width: 50px;
  height: 50px;
  padding: 10px 16px;
  font-size: 18px;
  line-height: 1.33;
  border-radius: 25px;
}
.btn-circle.btn-xl {
  width: 70px;
  height: 70px;
  padding: 10px 16px;
  font-size: 24px;
  line-height: 1.33;
  border-radius: 35px;
}
input{
	text-align: center;
}
</style>
