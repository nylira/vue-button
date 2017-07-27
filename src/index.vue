<template lang='pug'>
router-link.ni-btn(:to='to', v-if="type === 'link'", exact='')
  span(:class='btnClass')
    i(v-if='icon', :class="'ni-btn-icon material-icons'" aria-hidden='true') {{ icon }}
    span.ni-btn-value(v-if='value') {{ value }}
a.ni-btn(v-else-if="type === 'anchor'")
  span(:class='btnClass')
    i(v-if='icon', :class="'ni-btn-icon material-icons'" aria-hidden='true') {{ icon }}
    span.ni-btn-value(v-if='value') {{ value }}
button.ni-btn(:type='type', v-else='')
  span(:class='btnClass')
    i(v-if='icon', :class="'ni-btn-icon material-icons'" aria-hidden='true') {{ icon }}
    span.ni-btn-value(v-if='value') {{ value }}
</template>

<script>
export default {
  name: 'ni-btn',
  computed: {
    btnClass () {
      let value = 'ni-btn-container'
      if (this.iconPos) value += ` ni-btn-icon-${this.iconPos}`
      if (this.size) value += ` ni-btn-size-${this.size}`
      if (this.theme) value += ` ni-btn-theme-${this.theme}`
      return value
    }
  },
  props: ['value', 'icon', 'icon-pos', 'type', 'size', 'theme', 'to']
}
</script>

<style lang='stylus'>
@require '~@/styles/variables.styl'

.ni-btn
  padding 0
  border none
  background transparent
  text-decoration none !important
  -webkit-appearance none
  margin 0
  display inline-block
  font-size 16px

/* firefox fix - padding */
.ni-btn::-moz-focus-inner
  padding 0
  border 0

.ni-btn-container::before,
.ni-btn-container::after
  content ''
  flex 1 0 auto

.ni-btn-container
  font-family sans
  font-size 1rem !important
  font-weight 400
  height 2em
  line-height 1
  color txt !important
  padding 0 0.75em
  margin 0
  background app-bg
  border 1px solid bc
  cursor pointer
  user-select none
  display flex
  justify-content center
  align-items center
  -webkit-appearance none

.ni-btn-container:hover:enabled
  color txt
  text-decoration none

.ni-btn-icon
  font-size 1em
  line-height 1

.ni-btn-icon + .ni-btn-value
  padding-left 0.5em

.ni-btn-value
  white-space nowrap
  text-overflow ellipsis
  overflow hidden

/* disabled */
.ni-btn.disabled
.ni-btn[disabled]
  opacity 0.333
  cursor not-allowed
  user-select none
  pointer-events none
  color faint !important

  &:focus:enabled
    outline none

/* right aligned icons */
.ni-btn-container.ni-btn-icon-right
  flex-direction row-reverse

  .ni-btn-icon + .ni-btn-value
    padding-left 0
    padding-right 0.5em

/* sizes */
.ni-btn-container.ni-btn-size-sm
  font-size 0.75em
  height 1.5rem
  line-height 1rem
  padding 0 1rem

  i.fa, i.material-icons
    font-size 0.75rem
    line-height 1
  .ni-btn-value
    font-size 0.75rem

.ni-btn-container.ni-btn-size-lg
  font-size 1.125em !important
  height 3rem
  font-weight normal
  padding 0 1rem

.ni-btn-container.ni-btn-theme-alpha-black
  color #fff !important
  background rgba(0,0,0,0.2)
  border none

  &:hover:enabled
    background rgba(0,0,0,0.3)

  &:active:enabled
    background rgba(0,0,0,0.4)

.ni-btn-container.ni-btn-theme-tendermint
  color #fff !important
  background #1d61a5
  border none

  &:hover:enabled
    background #216eba

  &:active:enabled
    background #061423

// cosmos
.ni-btn-container.ni-btn-theme-cosmos
  background transparent
  border 2px solid bc-dim
  border-radius 0.25rem
  color txt
  font-family sans
  padding 0 1rem

.ni-btn:hover:enabled .ni-btn-container.ni-btn-theme-cosmos,
.ni-btn:focus:enabled .ni-btn-container.ni-btn-theme-cosmos
  border-color bc-hover

.ni-btn:active:enabled .ni-btn-container.ni-btn-theme-cosmos,
.ni-btn.router-link-active:enabled .ni-btn-container.ni-btn-theme-cosmos
  color bright !important
  border-color bc-active
</style>
