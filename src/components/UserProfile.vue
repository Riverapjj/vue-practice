<template>
    <div class="user-profile">
        <div class="user-profile__user-panel">
            <h1 class="user-profile__username"> @{{ user.username }}</h1>
            <div class="user-profile__admin-badge" v-if="user.isAdmin">
                Admin
            </div>
            <div class="user-profile__follower_count">
                <strong>Followers: {{ followers }}</strong>
            </div>
        </div>
        <div class="user-profile__twoots-wrapper">
            <TwootItem v-for="twoot in user.twoots" :key="twoot.id" :username="user.username" :twoot="twoot" />                          
        </div>
    </div>
</template>

<script>	
import TwootItem from "./TwootItem";

export default {
	name: 'UserProfile',
    components: { TwootItem },
	data() {
		return {
			followers: 0,
			user:{
                id: 1,
				username: 'riverapj_',
				firstName: 'Josue',
				lastName: 'Rivera',
				email: 'riverapj99@gmail.com',
				isAdmin: true,
                toowts: [
                    { id: 1, content: 'Twotter is Amaxing!'},
                    { id: 2, content: "Don't forget to suscribe"}
                ]
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
};
</script>

<style>
.user-profile {
    display: grid;
    grid-template-columns: 1fr 3fr;
    width: 100%;
    padding: 50px 5%;
}

.user-profile__user-panel {
    display: flex;
    flex-direction: column;
    margin-right: 50px;
    padding: 20px;
    background-color: white;
    border-radius: 5px;
    border: 1px solid #DFE4E8;
}

h1 {
    margin: 0;
}
.user-profile__admin-badge {
    background: rebeccapurple;
    border-radius: 5px;
    color: white;
    margin-right: auto;
    padding: 0 10px;
    font-weight: bold;
}     
</style>
