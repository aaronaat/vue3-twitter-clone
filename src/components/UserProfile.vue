<template>
    <div class="user-profile">

    <div class="panel">
        <h3>@{{ user.username }} - {{ fullName }} <br /></h3>

        <div class="user-isadmin" v-if="user.isAdmin">
        Admin
        </div>

        <button @click="followUser">Follow {{user.username}}</button>
        <br />

        <sub style="font-weight:bold;">Followers: {{ followers }} </sub>
    </div>

    </div>
</template>


<script>
    export default {
    name: 'UserProfile',
    data() {
    return {
        followers: 0,
        user: {
        id: 1,
        username: 'aaron_taylor',
        firstName: 'Aaron',
        lastName: 'Taylor',
        email: 'aarontaylor@gmail.com',
        isAdmin: true
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
        padding: 50px 5%;
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
</style>
