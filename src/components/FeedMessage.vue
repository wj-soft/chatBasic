<template>
    <div class="message--feed">
      <div class="message--feed__nickname"><span>name: </span>{{msg.user}}</div>
      <p class="message--feed__message">{{msg.message}}</p>
    </div>
</template>

<script>

export default {
  name: 'FeedMessage',
  props: ['msg'],
  data() {
    return {
    }
  },
  computed: {
  },
  methods: {
  }
}
</script>

<style>
.message--feed {
  width: 90%;
  min-height: 50px;
  margin: 15px auto;
  text-align: left;
  background: #f2eb9d;
}
.message--feed__nickname {
  background: #efe700;
  position: relative;
  right: 5px;
  bottom: 5px;
  border-radius: 10px;
  width: 120px;
  text-align: center;
  overflow: hidden;
}
.message--feed__nickname > span {
  font-weight: bold;
}
.message--feed__message {
  padding: 0 15px;
  margin: 0;
  word-break: break-all;
}
</style>

