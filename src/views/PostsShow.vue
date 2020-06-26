<template>
  <div class="posts-show">
    <section id="intro" class="wrapper style1">
    <div class="title">{{ post.title }}</div>
    <div class="container">
      <vue-audio :file="post.file"></vue-audio>
      <br>
      <div v-if="post.image_url" style="width:1100px; height:500px" v-bind:style="{ 'background-image': 'url(' + post.image_url + ')' }">
        <h2 v-on:click="goTo()">{{ post.title }} - {{ post.username }} </h2>
        <hr>
        <h4>genre: {{ post.genre }}</h4>
        <br>
        <h4>status: {{ post.status }}</h4>
        <br>
        <!-- <p><img v-bind:src="post.image_url"></p> -->
        <h3>{{ post.username }} is in {{ post.city }}, {{ post.state }}</h3>
        <br>
        <h1>Likes: {{ post.likes.length }}</h1>
        <br>
        <!-- <p>{{ post.comments}}</p> -->
        <h3>Comments:</h3>
        <div v-for="comment in post.comments">
          <h4>{{ comment.username }}: {{ comment.body }}</h4>
        </div>
        <ul class="actions">
          <li><button v-on:click="addLike()" class="button style3 large">Like</button></li>
          <li><button v-on:click="addComment()" class="button style3 large">Comment</button></li>
        </ul>
      </div>
      <br>
      <br>
      <br>
      <ul class="actions">
        <li><a href="/users/index" class="button style3 large">Looking for more creators in this area?</a></li>
      </ul>
      <br>
      <hr>
      <ul class="actions">
        <li><a href="/posts/new" class="button style3 large">Post a new song</a></li>
      </ul>
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
      post: {},
      currentPost: {},
      comments: [],
      likes: [],
      file: ""
    };
  },
  created: function() {
    // console.log(this.$route.params.id)
    axios.get('/api/posts/' + this.$route.params.id).then(response => {
      console.log(response.data);
      this.post = response.data;
    });
  },
  methods: {
    goTo: function() {
      console.log('slingshot engaged');
      this.$router.push(`/users/${this.post.user.id}`);
    },
    addLike: function() {
      // var params = {
      //   post_id: this.post.id,
      //   user_id: 6
      // };
      // axios.post("/api/likes").then(response => {
      //   console.log(response.data);
      //   this.$router.push(`/posts/${this.post.id}`);
      // });
      this.post.likes.length += 1;
    },
  },
  components:  {
    VueAudio
  },
};
</script>
