<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <h1> VueChat</h1>
    <make-nickname></make-nickname>
  </div>
</template>

<script>
import MakeNickname from '../components/MakeNickname';

export default {
  name: 'home',
  components: {
    MakeNickname
  }
}
</script>
