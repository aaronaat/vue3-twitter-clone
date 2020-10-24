<template>
    <div class="user-profile">

    <div class="panel">
        <h3>@{{ user.username }} - {{ fullName }} <br /></h3>

        <div class="user-isadmin" v-if="user.isAdmin">
        Admin
        </div>
        <div class="user-notadmin" v-else>
        Normal user
        </div>

        <button @click="followUser">Follow {{user.username}}</button>
        <br />

        <sub style="font-weight:bold;">Followers: {{ followers }} </sub>
    </div>

    <div class="postlist">

    <PostItem 
    v-for="post in user.posts" 
    :key="post.id" 
    :username="user.username" 
    :post="post" 
    @fav="toggleFav" />



    </div>
    </div>

    
</template>


<script>
import PostItem from "./PostItem";

    export default {
    name: 'UserProfile',

    components: { PostItem },
    data() {
        return {
            followers: 0,
            user: {
                id: 1,
                username: 'aaron_taylor',
                firstName: 'Aaron',
                lastName: 'Taylor',
                email: 'aarontaylor@gmail.com',
                isAdmin: true,
                posts: [
                    {id: 1, content: 'Hello world...'},
                    {id: 2, content: 'Goodbye world...'}
                ]
            }
        }
        },
        watch: {
        followers(newCount, oldCount) {
            if (oldCount < newCount) {
            console.log(`${this.user.username} gained a follower.`)
            }
        }
        },
        computed: {
        fullName() {
            return `${this.user.firstName} ${this.user.lastName}`;
        }
        },
        methods: {
        followUser() {
            this.followers++;
        },
        toggleFav(id) {
            console.log(`favorited post with id ${id}`)
        }
        },
        mounted() {
        this.followUser();
        }

    }
</script>

<style>
    .user-profile {
        font-family: Verdana, Arial;
        display:grid;
        grid-template-columns: 1fr 3fr;
        width: 100%;
        padding: 10px 3%;

    }
    .panel {
        display:flex;
        flex-direction: column;
        margin-right: 50px;
        padding: 20px;
        background-color: white;
        border-radius: 5px;
        border: 1px solid #DFE3E8;

    }
    .user-isadmin {
    background:green;
    color:lightgray;
    border-radius:4px;
    margin-right:auto;
    margin-bottom: 2px;
    padding: 0px 6px;
    font-weight:bold;
    }
    .user-notadmin {
    background:lightgray;
    color:green;
    border-radius:4px;
    margin-right:auto;
    margin-bottom: 2px;
    padding: 0px 6px;
    font-weight:bold;
    }

    .postlist  {
    display: grid;
    grid-gap: 10px;
    margin-bottom: auto;
    margin-right:80px;
  }
</style>
