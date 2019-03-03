<template>
    <div>
      <input type="text" placeholder="닉네임을 입력하세요" v-model="nickname">
      <button @click="enterChat()">입장하기</button>
    </div>
</template>

<script>

export default {
  name: 'MakeNickname',
  data() {
    return {
      nickname: ''
    }
  },
  computed: {
    nicknameValidator() {
      return this.nickname.length > 2
    }
  },
  methods: {
    enterChat() {
      if (!this.nicknameValidator) {
        alert('닉네임을 3자이상 입력해주세요')
        return
      }

      window.sessionStorage.setItem('nickname', this.nickname)
      this.$router.push({
        name: 'room'
      })
    },
    
  }
}
</script>
