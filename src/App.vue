<template>
	<div id="app">
		@{{ user.username }} - {{ fullName }}
		<strong>Followers: {{ followers }}</strong>
		<button v-on:click="followUser">follow

		</button>
	</div>
</template>

<script>	

export default {
	name: 'App',
	data() {
		return {
			followers: 0,
			user:{
				username: 'riverapj_',
				firstName: 'Josue',
				lastName: 'Rivera',
				email: 'riverapj99@gmail.com',
				isAdmin: true
			}
		}
	},
	watch: {
		followers(newFollowerCount, oldFollowerCount) {
			if(oldFollowerCount < newFollowerCount) {
				console.log(`${this.user.username} has gained a follower`)
			}
		}
	},
	computed: {
		fullName(){
			return `${this.user.firstName} ${this.user.lastName}`;
		}
	},
	methods: {
		followUser() {
			this.followers++
		}
	},
	mounted() {
		this.followUser();
	}
}	
</script>

<style>
#app {
	font-family: Avenir, Helvetica, Arial, sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	color: #2c3e50;
	display: flex;
	flex-direction: column;
	text-align: center;
}
</style>
