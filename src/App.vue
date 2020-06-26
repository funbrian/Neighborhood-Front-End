<template>
  <div id="app">
    <section id="header" class="wrapper">
 
    <!-- Logo -->
      <div id="logo">
        <h1><a href="index.html">Neighborhood</a></h1>
        <p>The music sharing and collaboration community of the future</p>
      </div>
    
    <!-- Nav -->
      <nav id="nav">
        <ul>
          <li class="current"><a href="/">Home</a></li>
          <li class="current"><a v-if="!isLoggedIn()" href="/login">Login</a></li>
          <li class="current"><a v-if="isLoggedIn()" href="/logout">Logout</a></li>
          <li class="current"><a v-if="!isLoggedIn()" href="/signup">Signup</a></li>
          <li class="current"><a href="/about">About</a></li>
          <li class="current"><a href="/posts/new">Post a new song</a></li>
        </ul>
      </nav>

    
    </section>
    
    <!-- Intro -->
    <!-- <section id="intro" class="wrapper style1">
    <div class="title">Timeline</div>
    <div class="container">
      <div v-bind:key="post.id" v-for="post in posts">
        <p v-on:click="goTo(post)">{{ post.title }} by {{ post.username }} ({{ post.status }})</p>
        <p>Genre: {{ post.genre }}</p> -->
        <!-- <br> -->
        <!-- <hr>
      </div>
      <ul class="actions">
        <li><a href="/posts/new" class="button style3 large">Post a new song</a></li>
      </ul>
    </div>
    </section> -->
    
    <!-- Main -->
    <!-- <section id="main" class="wrapper style2">
    <div class="title"></div>
    <div class="container">
    
      Image
    
      Features
        <section id="features">
          <header class="style1">
            <h2>Dolor consequat feugiat amet veroeros</h2>
            <p>Feugiat dolor nullam orci pretium phasellus justo</p>
          </header>
          <div class="feature-list">
            <div class="row">
              <div class="col-6 col-12-medium">
                <section>
                  <h3 class="icon fa-comment">Mattis velit diam vulputate</h3>
                  <p>Eget mattis at, laoreet vel et velit aliquam diam ante, aliquet sit amet vulputate et magna feugiat laoreet vel velit lorem.</p>
                </section>
              </div>
              <div class="col-6 col-12-medium">
                <section>
                  <h3 class="icon solid fa-sync">Lorem ipsum dolor sit veroeros</h3>
                  <p>Eget mattis at, laoreet vel et velit aliquam diam ante, aliquet sit amet vulputate et magna feugiat laoreet vel velit lorem.</p>
                </section>
              </div>
              <div class="col-6 col-12-medium">
                <section>
                  <h3 class="icon fa-image">Pretium phasellus justo lorem</h3>
                  <p>Eget mattis at, laoreet vel et velit aliquam diam ante, aliquet sit amet vulputate et magna feugiat laoreet vel velit lorem.</p>
                </section>
              </div>
              <div class="col-6 col-12-medium">
                <section>
                  <h3 class="icon solid fa-cog">Tempus sed pretium orci</h3>
                  <p>Eget mattis at, laoreet vel et velit aliquam diam ante, aliquet sit amet vulputate et magna feugiat laoreet vel velit lorem.</p>
                </section>
              </div>
              <div class="col-6 col-12-medium">
                <section>
                  <h3 class="icon solid fa-wrench">Aliquam consequat et feugiat</h3>
                  <p>Eget mattis at, laoreet vel et velit aliquam diam ante, aliquet sit amet vulputate et magna feugiat laoreet vel velit lorem.</p>
                </section>
              </div>
              <div class="col-6 col-12-medium">
                <section>
                  <h3 class="icon solid fa-check">Dolore laoreet aliquam mattis</h3>
                  <p>Eget mattis at, laoreet vel et velit aliquam diam ante, aliquet sit amet vulputate et magna feugiat laoreet vel velit lorem.</p>
                </section>
              </div>
            </div>
          </div>
          <ul class="actions special">
            <li><a href="#" class="button style1 large">Get Started</a></li>
            <li><a href="#" class="button style2 large">More Info</a></li>
          </ul>
        </section>
    
    </div>
    </section> -->
    
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
    <section id="footer" class="wrapper">
      <div class="title">The Rest Of It</div>
      <div class="container">
        <header class="style1">
          <h2>Join the Neighborhood!</h2>
          <p>
            Don't hesitate to reach out to us if you have any questions or suggestions.
          </p>
        </header>
        <div class="row">
          <div class="col-6 col-12-medium">
      
            <!-- Contact Form -->
              <section>
                <form method="post" action="#">
                  <div class="row gtr-50">
                    <div class="col-6 col-12-small">
                      <input type="text" name="name" id="contact-name" placeholder="Name" />
                    </div>
                    <div class="col-6 col-12-small">
                      <input type="text" name="email" id="contact-email" placeholder="Email" />
                    </div>
                    <div class="col-12">
                      <textarea name="message" id="contact-message" placeholder="Message" rows="4"></textarea>
                    </div>
                    <div class="col-12">
                      <ul class="actions">
                        <li><input type="submit" class="style1" value="Send" /></li>
                        <li><input type="reset" class="style2" value="Reset" /></li>
                      </ul>
                    </div>
                  </div>
                </form>
              </section>
      
          </div>
          <div class="col-6 col-12-medium">
      
            <!-- Contact -->
              <section class="feature-list small">
                <div class="row">
                  <div class="col-6 col-12-small">
                    <section>
                      <h3 class="icon solid fa-home">Mailing Address</h3>
                      <p>
                        Neighborhood HQ<br />
                        1 Willoughby Way<br />
                        Burlington, VT 05401
                      </p>
                    </section>
                  </div>
                  <div class="col-6 col-12-small">
                    <section>
                      <h3 class="icon solid fa-comment">Social</h3>
                      <p>
                        <a href="#">@neighborhood</a><br />
                        <a href="#">linkedin.com/neighborhood</a><br />
                        <a href="#">facebook.com/neighborhood</a>
                      </p>
                    </section>
                  </div>
                  <div class="col-6 col-12-small">
                    <section>
                      <h3 class="icon solid fa-envelope">Email</h3>
                      <p>
                        <a href="#">info@neighborhood.com</a>
                      </p>
                    </section>
                  </div>
                  <div class="col-6 col-12-small">
                    <section>
                      <h3 class="icon solid fa-phone">Phone</h3>
                      <p>
                        (999) 867-5309
                      </p>
                    </section>
                  </div>
                </div>
              </section>
      
          </div>
        </div>
        <div id="copyright">
          <ul>
            <li>&copy; Untitled.</li><li>Design: <a href="http://html5up.net">HTML5 UP</a></li>
          </ul>
        </div>
      </div>
    </section>
  </div>
</template>

<style>

</style>

<script>
import axios from "axios";

export default {
  data: function () {
    return {
      titleFilter: "",
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
      this.$router.push("`/posts/${post.id}`")
    }
  }
};
</script>