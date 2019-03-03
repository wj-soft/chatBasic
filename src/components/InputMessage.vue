<template>
    <div class="input--message">
      <input type="text" @keyup.enter="sendMessage()" placeholder="메세지를 입력하세요" v-model="message">
    </div>
</template>

<script>
export default {
  name: 'InputMessage',
  data() {
    return {
      message: '',
    }
  },
  computed: {
  },
  methods: {
    sendMessage() {
      this.$emit('sendMessage', this.message);
      this.message = '';
    }
  }
}
</script>

<style>
.input--message {
  position: fixed;
  left: 0;
  right: 0;
  bottom: 5%;
}
.input--message > input[type="text"] {
  border-radius: 10px;
  width: 100%;
  max-width: 400px;
  height: 40px;
}

.input--message > input[type="text"]::placeholder { 
  font-size: 1.5em;
  text-align: center;
}
</style>
