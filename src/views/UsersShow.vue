<template>
  <div class="users-show">
    <section id="intro" class="wrapper style1">
    <div class="title1"></div>
    <div class="container">
      <h1 v-on:click="goTo()">{{ user.first_name }} {{ user.last_name }}</h1>
      <h1>Username: {{ user.username }}</h1>
      <!-- <h2>{{ user.username }}</h2> -->
      <h1>{{ user.city }}, {{ user.state }}</h1>
      <h1>Following: {{ user.followees.length }} Followers: {{ user.followers.length }}</h1> 
      <!-- <h1>Followers: {{ user.followers.length }}</h1> -->
      <h1>Posts: {{ user.posts.length }}</h1>
      <ul class="actions">
        <li><a href="/api/follow/new" class="button style3 large">Follow</a></li>
      </ul>
      <br>
      <br>
      <br>
      <div v-for="post in user.posts">
        <div v-if="post.image_url" style="width:1100px; height:250px" v-bind:style="{ 'background-image': 'url(' + post.image_url + ')' }">
          <h4>{{ post.title }} ({{ post.status }})</h4>
          <vue-audio :file="post.file"></vue-audio>
          <ul class="actions">
            <li><button v-on:click="addLike()" class="button style3 large">Like</button></li>
            <li><button v-on:click="addComment()" class="button style3 large">Comment</button></li>
          </ul>
          <br>
        </div>
        <br>
      </div>
      <ul class="actions">
        <li><a href="#" class="button style3 large">Want to Collaborate? Send {{ user.username }} a message!</a></li>
      </ul>
      <!-- <div v-bind:key="this.user.post.id" v-for="this.user.post in this.user.posts">
        <p>{{ this.user.post.title }} ({{ this.user.post.status }})</p>
        <p>Genre: {{ this.user.post.genre }}</p>
      </div> -->
      <!-- <br> -->
      <hr>
    </div>
    </section>
  </div>
</template>

<style>
</style>

<script>
import axios from "axios";
import VueAudio from 'vue-audio';

export default {
  data: function() {
    return {
      message: "Welcome to the show!",
      user: {},
      post: {},
      posts: [],
      currentPost: {},
      comments: [],
      likes: [],
      file: ""
    };
  },
  created: function() {
    // console.log(this.$route.params.id)
    axios.get('/api/users/' + this.$route.params.id).then(response => {
      console.log(response.data);
      this.user = response.data;
    });
  },
  methods: {
    goTo: function() {
      this.$router.push(`/users/${this.user.id}`);
    }
  },
  components:  {
    VueAudio
  },
};
</script>

