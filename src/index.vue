<template lang='pug'>
router-link.ni-btn(:to='to' v-if="type === 'link'" exact)
  span(:class='btnClass')
    i(v-if='icon', :class="'ni-btn__icon material-icons'" aria-hidden='true') {{ icon }}
    span.ni-btn__value(v-if='value') {{ value }}
a.ni-btn(v-else-if="type === 'anchor'")
  span(:class='btnClass')
    i(v-if='icon', :class="'ni-btn__icon material-icons'" aria-hidden='true') {{ icon }}
    span.ni-btn__value(v-if='value') {{ value }}
button.ni-btn(:type='type' v-else)
  span(:class='btnClass')
    i(v-if='icon', :class="'ni-btn__icon material-icons'" aria-hidden='true') {{ icon }}
    span.ni-btn__value(v-if='value') {{ value }}
</template>

<script>
export default {
  name: 'ni-btn',
  computed: {
    btnClass () {
      let value = 'ni-btn__container'
      if (this.iconPos) value += ` ni-btn__icon-${this.iconPos}`
      if (this.size) value += ` ni-btn--size-${this.size}`
      if (this.theme) value += ` ni-btn--theme-${this.theme}`
      if (this.type) value += ` ni-btn--`${this.type}`
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

.ni-btn__container::before,
.ni-btn__container::after
  content ''
  flex 1 0 auto

.ni-btn__container
  font-family sans
  font-size 1rem !important
  font-weight 400
  height 2em
  line-height 1
  color txt !important
  padding 0 0.75em
  margin 0
  background app-bg
  border 2px solid bc
  border-radius 0.25rem
  cursor pointer
  user-select none
  display flex
  justify-content center
  align-items center
  -webkit-appearance none

.ni-btn__container:hover:enabled
  color txt
  text-decoration none
  border-color bc-bright
  background app-fg

.ni-btn__icon
  font-size 1em
  line-height 1

.ni-btn__icon + .ni-btn__value
  padding-left 0.375em

.ni-btn__value
  font-weight 300
  white-space nowrap
  text-overflow ellipsis
  overflow-x hidden

/* disabled */
.ni-btn.disabled
.ni-btn[disabled]
  opacity 0.333
  cursor not-allowed
  user-select none
  pointer-events none
  color dim !important

  &:focus:enabled
    outline none

/* right aligned icons */
.ni-btn__container.ni-btn__icon-right
  flex-direction row-reverse

  .ni-btn__icon + .ni-btn__value
    padding-left 0
    padding-right 0.5em

/* sizes */
.ni-btn__container.ni-btn--size-sm
  font-size 0.75em
  height 1.5rem
  line-height 1rem
  padding 0 1rem

  i.fa, i.material-icons
    font-size 0.75rem
    line-height 1
  .ni-btn__value
    font-size 0.75rem

.ni-btn__container.ni-btn--size-lg
  font-size 1.125em !important
  height 3rem
  font-weight normal
  padding 0 1rem

.ni-btn__container.ni-btn--theme-alpha-black
  color #fff !important
  background rgba(0,0,0,0.2)
  border none
  border-radius 0

  &:hover:enabled
    background rgba(0,0,0,0.3)

  &:active:enabled
    background rgba(0,0,0,0.4)

.ni-btn__container.ni-btn--theme-tendermint
  color #fff !important
  background #1d61a5
  border none
  border-radius 0

  &:hover:enabled
    background #216eba

  &:active:enabled
    background #061423

.ni-btn.ni-btn--primary
  .ni-btn__container
    background darken(link, 10%)
    border-color darken(link, 25%)
    &:hover
      background link
      border-color darken(link, 12.5%)
    .ni-btn__value
      color bright
</style>
