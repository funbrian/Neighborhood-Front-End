<template>
  <div class="posts-new">
    <div class="container">      
      <form v-on:submit.prevent="submit()">
        <h1>Post a new song</h1>
        <ul>
          <li class="text-danger" v-for="error in errors">{{ error }}</li>
        </ul>
        <div class="form-group">
          <label>Title:</label> 
          <input type="text" class="form-control" v-model="title">
        </div>
        <div class="form-group">
          <label>Genre:</label>
          <input type="text" class="form-control" v-model="genre">
        </div>
        <div class="form-group">
          <label>Status:</label>
          <input type="text" class="form-control" v-model="status">
        </div>
        <div class="form-group">
          <label>File</label>
          <input type="text" class="form-control" v-model="file">
          <br>
          <ul class="actions">
            <li><a href="#" class="button style3 large">Browse</a></li>
          </ul>
        </div>

        <!-- <textarea rows="30" cols="80"></textarea> -->

        <div class="form-group">
          <label>Image Url:</label>
          <input type="text" class="form-control" v-model="imageUrl">
        </div>
        <input type="submit" class="btn btn-primary" value="Submit">
      </form>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data: function() {
    return {
      title: "",
      genre: "",
      status: "",
      file: "",
      imageUrl: "",
      errors: []
    };
  },
  methods: {
    submit: function() {
      var params = {
        title: this.title,
        genre: this.genre,
        status: this.status,
        file: this.file,
        image_url: this.imageUrl
      };
      axios
        .post("/api/posts", params)
        .then(response => {
          this.$router.push("/posts");
        })
        .catch(error => {
          this.errors = error.response.data.errors;
        });
    }
  }
};
</script>