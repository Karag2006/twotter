<template>
  <div id="app">
    @{{ user.username }} - {{ fullName }}<br>
    <strong>Followers : </strong> {{followers}}
    <button @click="followUser">
      Follow
    </button>
  </div>
</template>

<script>

export default {
  name: 'App',
  data() {
    return {
      followers: 0,
      user: {
        id: 1,
        username: "karag2006",
        firstname: "Martin",
        lastname: "Richter",
        email: "martin.richter2006@gmail.com",
        isAdmin: true,
      }
    }
  },
  watch: {
    followers(newFollowerCount, oldFollowerCount) {
      if (oldFollowerCount < newFollowerCount) {
        console.log(this.user.username + ' has gained a follower!');
      }
    }
  },
  computed: {
    fullName() {
      return (this.user.firstname + ' ' + this.user.lastname);
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
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  display: flex;
  flex-direction: column;
}
</style>
