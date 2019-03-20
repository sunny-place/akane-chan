<template lang="pug">
  .bl_logs_wrap
    ul.bl_logs
      li.bl_logs_item(v-for="item in list") {{item.text}}
</template>
<script>
export default {
  name: 'Log',
  props: ['list']
}
</script>
<style lang="stylus" scoped>
.bl_logs
  width 100%
  height 100%
  padding 0
  margin 0
  box-sizing border-box
  display flex
  flex-flow column nowrap
  justify-content flex-end
  &_wrap
    width 100%
    height 100%
    overflow-y auto
  &_item
    list-style none
    width 100%
    box-sizing border-box
    padding 5px 10px
    border solid 2px #ffc8c3
    margin-bottom 10px
    border-radius 10px
    color #333
</style>

