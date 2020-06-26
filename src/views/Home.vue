<!-- template>
  <!-- <div class="posts-index">
    <div v-bind:key="post.id" v-for="post in posts">
      <p v-on:click="goTo(post)">{{ post.title }} by {{ post.username }} ({{ post.status }})</p>
      <p>Genre: {{ post.genre }}</p> -->
      <!-- <br> -->
      <!-- <hr>
    </div> -->


    <!-- <datalist id="titles">
      <option v-for="post in posts">{{ post.title }}</option>
    </datalist> -->


    <!-- <button v-on:click="setSortAttribute()">Most Recent</button>
    <button v-on:click="setOtherAttribute()">Title</button> -->
    <!-- <div v-for="post in orderBy(posts, sortAttribute, 1)" v-on:click="currentPost = post" v-bind:class="{selected: currentPost === post}">
      <p>title: <a v-bind:href="`/api/posts/${post.id}`">{{ post.title }}</a></p>
      <hr>
    </div> -->
  <!-- </div>
</template>


<style>
  .selected {
    color: yellow;
    background-color: maroon;
  }
</style>

<script>
import Vue2Filters from "vue2-filters";

import axios from "axios";

export default {
  mixins: [Vue2Filters.mixin],
  data: function() {
    return {
      message: "Welcome to Vue.js!",
      posts: [],
      currentPost: {},
      createdFilter: '',
      user: "",
      sortAttribute: "created_at"
    };
  },
  created: function() {
    axios.get('/api/posts').then(response => {
      console.log(response.data);
      this.posts = response.data;
    });
  },
  methods: {
    setSortAttribute: function() {
      console.log('slingshot engaged...');
      this.sortAttribute = 'created_at';
    },
    setOtherAttribute: function() {
      console.log('slingshot engaged...');
      this.sortAttribute = 'title';
    },
    goTo: function() {} -->
    <!-- // user: function() {
    //   this.user = (Users.where (id = post.user_id))
    // }
  }
};
</script> -->

<template>
  <div class="posts-index">
    <section id="intro" class="wrapper style1">
    <div class="title">Timeline</div>
    <div class="container">
      <div v-bind:key="post.id" v-for="post in posts">
        <div v-if="post.image_url" style="width:1100px; height:250px" v-bind:style="{ 'background-image': 'url(' + post.image_url + ')' }">
          <p v-on:click="goTo(post)">"{{ post.title }}" by {{ post.username }} ({{ post.status }}) </p>
          <p>Genre: {{ post.genre }}</p>
          <vue-audio :file="post.file"></vue-audio>
          <ul class="actions">
            <li><a href="/test" class="button style3 large">Comment</a></li>
            <li><a href="/test" class="button style3 large">Like</a></li>
          </ul>
        </div>
        <!-- <br> -->
        <hr>
      </div>
      <ul class="actions">
        <li><a href="/posts/new" class="button style3 large">Post a new song</a></li>
      </ul>
    </div>
    </section>
    
    <!-- Main -->
    
    <!-- Highlights -->
    <!-- <section id="highlights" class="wrapper style3">
    <div class="title">The Endorsements</div>
    <div class="container">
      <div class="row aln-center">
        <div class="col-4 col-12-medium">
          <section class="highlight">
            <a href="#" class="image featured"><img src="images/pic02.jpg" alt="" /></a>
            <h3><a href="#">Aliquam diam consequat</a></h3>
            <p>Eget mattis at, laoreet vel amet sed velit aliquam diam ante, dolor aliquet sit amet vulputate mattis amet laoreet lorem.</p>
            <ul class="actions">
              <li><a href="#" class="button style1">Learn More</a></li>
            </ul>
          </section>
        </div>
        <div class="col-4 col-12-medium">
          <section class="highlight">
            <a href="#" class="image featured"><img src="images/pic03.jpg" alt="" /></a>
            <h3><a href="#">Nisl adipiscing sed lorem</a></h3>
            <p>Eget mattis at, laoreet vel amet sed velit aliquam diam ante, dolor aliquet sit amet vulputate mattis amet laoreet lorem.</p>
            <ul class="actions">
              <li><a href="#" class="button style1">Learn More</a></li>
            </ul>
          </section>
        </div>
        <div class="col-4 col-12-medium">
          <section class="highlight">
            <a href="#" class="image featured"><img src="images/pic04.jpg" alt="" /></a>
            <h3><a href="#">Mattis tempus lorem</a></h3>
            <p>Eget mattis at, laoreet vel amet sed velit aliquam diam ante, dolor aliquet sit amet vulputate mattis amet laoreet lorem.</p>
            <ul class="actions">
              <li><a href="#" class="button style1">Learn More</a></li>
            </ul>
          </section>
        </div>
      </div>
    </div>
    </section> -->
    <!-- <p v-if="isLoggedIn()">I am Logged in</p> -->
    <!-- <p v-else-if="!isLoggedIn()">I am NOT Logged in</p> -->
    <router-view/>
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
      titleFilter: "",
      posts: [],
      post: {},
      currentPost: {},
      createdFilter: '',
      user: "",
      username: "",
      sortAttribute: "created_at",
      file: ""
    };
  },
  created: function() {
    axios.get('/api/posts').then(response => {
      console.log(response.data);
      this.posts = response.data;
    });
  },
  methods: {
    isLoggedIn: function() {
      console.log(' i am checking if i\'m logged in');
      if (localStorage.getItem("jwt")) {
        return true
      } else {
        return false
      }
    },
    getUserId: function() {
      return parseInt(localStorage.getItem("user_id"));
    },
    goTo: function(post) {
      this.$router.push(`/posts/${post.id}`);
    }
  },
  components:  {
    VueAudio
  },
};
</script>