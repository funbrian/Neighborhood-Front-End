<template>
  <div class="signup">
    <div class="container">
      <form v-on:submit.prevent="submit()">
        <h1>Signup</h1>
        <ul>
          <li class="text-danger" v-for="error in errors">{{ error }}</li>
        </ul>
        <img v-if="status" v-bind:src="`https://http.cat/${status}`">
        <div class="form-group">
          <label>First Name:</label> 
          <input type="text" class="form-control" v-model="first_name">
          <small v-if="first_name.length <=20">{{ 20 - first_name.length }} characters remaining</small>
          <small v-if="first_name.length > 20">First name must be a max of 20 characters</small>
        </div>
        <div class="form-group">
          <label>Last Name:</label> 
          <input type="text" class="form-control" v-model="last_name">
          <small v-if="last_name.length <=20">{{ 20 - last_name.length }} characters remaining</small>
          <small v-if="last_name.length > 20">Last name must be a max of 20 characters</small>
        </div>
        <div class="form-group">
          <label>Email:</label>
          <input type="email" class="form-control" v-model="email">
        </div>
        <div class="form-group">
          <label>City:</label>
          <input type="city" class="form-control" v-model="city">
        </div>
        <div class="form-group">
          <label>State:</label>
          <input type="state" class="form-control" v-model="state">
        </div>
        <div class="form-group">
          <label>Username:</label>
          <input type="username" class="form-control" v-model="username">
        </div>
        <div class="form-group">
          <label>Password:</label>
          <input type="password" class="form-control" v-model="password">
        </div>
        <div class="form-group">
          <label>Password confirmation:</label>
          <input type="password" class="form-control" v-model="passwordConfirmation">
          <small v-if="password != passwordConfirmation" class="text-danger">Password Confirmation must match Password</small>
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
      first_name: "",
      last_name: "",
      email: "",
      city: "",
      state: "",
      username: "",
      password: "",
      passwordConfirmation: "",
      errors: [],
      status: ""
    };
  },
  methods: {
    submit: function() {
      var params = {
        first_name: this.first_name,
        last_name: this.last_name,
        email: this.email,
        username: this.username,
        city: this.city,
        state: this.state,
        password: this.password,
        password_confirmation: this.passwordConfirmation
      };
      axios
        .post("/api/users", params)
        .then(response => {
          this.$router.push("/login");
        })
        .catch(error => {
          this.errors = error.response.data.errors;
          this.status = error.response.status;
        });
    }
  }
};
</script>



