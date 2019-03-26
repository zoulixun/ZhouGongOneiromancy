<template>
  <div id="app">
    <img src="./assets/bagua.jpg" width="300">
		<h1 class="text-muted">邹公解梦</h1>
		<MyDream v-on:formSubmit="dreamCause"></MyDream>
		<DreamCause v-html:mydreamCause="dreamResult"></DreamCause>
		<Copyright></Copyright>
  </div>
</template>

<script>
	import MyDream from './components/MyDream.vue'
	import DreamCause from './components/DreamCause.vue'
	import Copyright from './components/Copyright.vue'
	
export default {
  name: 'App',
	data(){
		return{
			dreamResult:""
		}
	},
	components:{
		MyDream,
		DreamCause,
		Copyright
	},
	methods:{
		dreamCause(dream){
			this.$http.get('https://api.apishop.net/common/dream/searchDreamDetail?apiKey=6ErUPyh56bea42faf45461ca4e0c48036a52dcb0ad5e846&keyword='+dream+'')
			.then((response) =>{
				if(response.body.result==null){
					this.dreamResult = "你的梦太奇怪了，我竟然解不了！"
	}
				this.dreamResult = response.body.result[0].content;
				localStorage.setItem('results',response.body.result[0].content);
			})
	//	this.dreamResult = localStorage.getItem('results');
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
h1{
	text-shadow:black 1px 1px 5px !important; 
}
</style>
