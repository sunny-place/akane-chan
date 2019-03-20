<template lang="pug">
  #app
    .ly_content
      .ly_charactor
        Character(:msg="msg")
      .ly_log
        Log(:list="log")
      .ly_input
        Input(v-on:submit="submit")
</template>

<script>
import Input from './components/Input.vue'
import Log from './components/Log.vue'
import Character from './components/Character.vue'

export default {
  name: 'app',
  data() {return{
    log: [
    ],
    msg: ""
  }},
  methods: {
    submit(said) {
      this.log.push({from: "1", text: said});
      const reply = this.getReply(said);
      this.msg = reply;
      this.log.push({from: "0", text: reply});
    },
    getReply(said) {
      if(/^[聞き]いて/.test(said)) {
        return "なんや";
      } else if (/[?？]$/.test(said)) {
        const list = ["わかる","せやな","それな"];
        return list[Math.floor( Math.random() * list.length )]
      } else {
        if(Math.random() > 0.2) {
          return "うん";
        } else {
          return "うん？"
        }
      }
    }
  },
  components: {
    Input,
    Log,
    Character
  }
}
</script>

<style lang="stylus">
html,body
  height 100%
  margin 0
  padding 0
  background-color #ffc8c3
#app
  height 100%
.ly_content
  background #fff
  max-width 1000px
  width 95%
  height 100%
  padding 30px
  box-sizing border-box
  margin auto
  border-left 1px solid #ffc8c3
  border-right 1px solid #ffc8c3
  position relative
.ly_input
  position absolute
  bottom 20px
  right 20px
  width calc(100% - 40px)
.ly_log
  padding-bottom 150px
  width 70%
  margin-right 0
  margin-left auto
  box-sizing border-box
  height 100%
  // overflow-y scroll

</style>
