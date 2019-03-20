<template lang="pug">
  div.bl_input
    input.bl_input_text(type="text" @keyup.enter="send" v-model="say")
    button.bl_input_submit(@click="send") しゃべる
</template>

<script>
export default {
  name: 'Input',
  data() {return{
    say : "",
  }},
  methods: {
    send() {
      if(this.say) {
        this.$emit('submit', this.say);
        this.say = "";
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="stylus" scoped>
.bl_input
  width 100%
  box-sizing border-box
  background-color #ffc8c3
  padding 20px
  border-radius 10px
  display flex
  align-items stretch
  &_text
    width 100%
    margin-right 10px
    border none 
    border-radius 10px
    padding 0 20px
    font-size 20px
  &_submit
    width 200px
    margin 0
    background #fff
    border solid 5px #fff
    color #ffc8c3
    font-weight bold
    border-radius 10px
    font-size 20px
    padding 10px
    cursor pointer
</style>
