<template>
  <div id="app">
    <main class="main-container">
      <div class="chat-timeline">
        <Item v-for="(chat, index) in chatLog" :speaker="chat.speaker" :name="chat.name" :message="chat.message" :key="index"/>
      </div>
      <InputForm @submitted="submit" />
    </main>
  </div>
</template>

<script>
import Item from './components/Item'
import InputForm from './components/InputForm'

export default {
  name: 'App',
  components: {
    Item,
    InputForm
  },
  data: () => {
    return {
      chatLog: [
        {name: 'ガッキー', speaker: 'other', message: '今日なにしたの？？'}
      ]
    }
  },
  methods: {
    submit (item) {
      this.chatLog.push({name: 'じぶん', speaker: 'me', message: item})
      this.botSubmit(item.endsWith('た'))
      this.scrollDown()
    },
    botSubmit (isEnd) {
      setTimeout(() => {
        if (isEnd) {
          this.chatLog.push({name: 'ガッキー', speaker: 'other', message: 'えらいね'})
          setTimeout(() => {this.chatLog.push({name: 'ガッキー', speaker: 'other', message: 'おつかれさま'})}, 2000)
        } else {
          this.chatLog.push({name: 'ガッキー', speaker: 'other', message: 'うん'})
        }
        this.scrollDown()
      }, 1000)
    },
    scrollDown () {
      const target = this.$el.querySelector('.chat-timeline')
      setTimeout(() => {
        const height = target.scrollHeight - target.offsetHeight
        target.scrollTop += 10
        if (height > target.scrollTop) {
          this.scrollDown()
        }
      }, 0)
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /*text-align: center;*/
  color: #2c3e50;
  margin-top: 60px;
}
</style>
