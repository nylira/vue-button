<template>
  <button class="pz-button" :type="btnType">
    <i v-if="btnIcon" :class="'fa fa-' + btnIcon" aria-hidden="true"></i>
    <span class="value" v-if="btnValue">{{ btnValue }}</span>
  </button> 
</template>
<script>
export default {
  name: 'pz-button',
  props: ['btn-value', 'btn-icon', 'btn-type']
}
</script>

<style lang="stylus">
ibc = #ccc
bc = #e0e0e0
txt = #000
dim = #666
light = #999
c-app-bg = hsl(0,0%,98%)
c-app-fg = #fff

button::before,
button::after
  content ''
  flex 1 0 auto

btn()
  background subtle-gradient
  border 1px solid ibc
  box-shadow inset hsla(0,0,100%,0.5) 0 0 0.5em

  padding 0 0.75em
  margin 0

  df()
  font-weight 400
  height 2em
  line-height 1

  cursor pointer
  user-select none

  display flex
  justify-content center
  align-items center
  -webkit-appearance none

  text-align center

  &:hover
    background subtle-gradient-hover
    box-shadow inset #fff 0 0 0.75em
    color #000
    text-decoration none

  &.disabled
  &[disabled]
    opacity 0.333
    cursor not-allowed
    user-select none
    color light
    &:focus
      outline none

  i.fa
    font-size 1em
    line-height 1

  i.fa + .value
    padding-left 0.5em

.pz-button
  btn()

  &.pz-button-link
    border-color transparent
    background transparent
    box-shadow none
    color link
    padding 0 0.5em
    &:hover
      background transparent
      box-shadow none

  &.pz-button-small
    height 1.5em
    font-size 0.75em
    line-height 1em
    padding 0 1em

    i.fa
      font-size 0.75em
      line-height 1

  &.pz-button-large
    height 3em
    font-size 1.25em
    font-weight normal
    padding 0 1em
</style>
