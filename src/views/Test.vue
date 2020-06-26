<template>
  <div class="test">
   <vue-audio :file="file1"></vue-audio>
   <br>
   <br>
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
      file1: 'src/assets/2percent.mp3'
    };
  },
  components:  {
    'vue-audio': VueAudio
  },
};
</script>

