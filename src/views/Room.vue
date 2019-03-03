<template>
  <div class="room">
    <h1 class="room--title">채팅방</h1>
    <div class="chat--body" id="chating">
      <feed-message v-for="(msg, index) in messages" :key="index" :msg="msg"></feed-message>
    </div>
    <input-message v-on:sendMessage="sendMessage"></input-message>
  </div>
</template>

<script>
import io from 'socket.io-client';
import FeedMessage from '../components/FeedMessage';
import InputMessage from '../components/InputMessage';

export default {
  name: 'room',
  components: {
    FeedMessage,
    InputMessage
  },
  data() {
    return {
      myName: '',
      messages: [],
      socket : io('localhost:3001')
    }
  },
  methods: {
    sendMessage(message) {
      this.socket.emit('SEND_MESSAGE', {
        user: this.myName,
        message
      });
      this.downScroll();
    },
    downScroll() {
      const area = window.document.getElementById('chating')
      area.scrollTop = area.scrollHeight;
    }
  },
  beforeRouteEnter (to, from, next) {
    if (!window.sessionStorage.getItem('nickname')) {
      return false;
    }
    next(() => {});
  },
  created() {
    this.myName = window.sessionStorage.getItem('nickname')
  },
  mounted() {
    this.socket.on('MESSAGE', (data) => {
        this.messages = [...this.messages, data];
    });

  }
}
</script>

<style scoped>
.room {
  background : #e3eae4;
  max-width: 500px;
  height: 100vh;
  margin: 0 auto;
}
.room--title {
  background: #454731;
  color: #ffff;
}
.chat--body {
  height: 80%;
  overflow: scroll;
}
</style>

