<script >
import { ref } from 'vue'

export default {
  name: 'HelloWorld',
  data() {
    return {
      messages: [],
      newMessage: '',
    };
  },
  methods: {
    sendMessage() {
      // console.log(this.newMessage)
      if (!this.newMessage) return;
      const message = {
        id: this.messages.length + 1,
        text: this.newMessage,
        isMe: true,
      };
      this.messages.push(message);
      this.newMessage = '';

      // Gemini API 호출 및 응답 처리
      // ...

      const response = {
        text: 'Gemini의 응답입니다.',
        isMe: false,
      };
      this.messages.push(response);
    },
  },
}

</script>

<template>
  <div>
    <div><h1>응답화면입니다.</h1></div>
        <div class="chat-area">
          <div v-for="message in messages" :key="message.id">
            <div class="message-box" :class="{ 'my-message': message.isMe }">
              <div class="message-text">{{ message.text }}</div>
            </div>
          </div>
        </div>
        <input type="text" v-model="newMessage" />
        <!-- <v-text-field v-model="newMessage" label="메시지 입력">11</v-text-field> -->
        <button @click="sendMessage">보내기</button>
        <!-- <v-btn @click="sendMessage">보내기</v-btn> -->
      
  </div>
</template>

<style>
.container {
  max-width: 800px;
  margin: 0 auto;
}
.chat-area {
  height: 400px;
  overflow-y: auto;
}
.message-box {
  padding: 10px;
  border-radius: 10px;
  margin: 10px 0;
}
.my-message {
  background-color: #eee;
  float: right;
}
.message-text {
  white-space: pre-wrap;
}
</style>
