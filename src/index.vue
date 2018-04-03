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
    img(v-if='!icon && img', :src="img" :class="'ni-btn__img'" aria-hidden='true')
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
      if (this.color) value += ` ni-btn--${this.color}`
      return value
    }
  },
  props: ['value', 'icon', 'icon-pos', 'img', 'type', 'size', 'theme', 'to', 'color']
}
</script>

<style lang='stylus'>
@require '~variables'

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
  color var(--txt, #333) !important
  padding 0 0.75em
  margin 0
  background var(--app-bg, #fff)
  border 2px solid var(--bc, #ddd)
  border-radius 0.25rem
  cursor pointer
  user-select none
  display flex
  justify-content center
  align-items center
  -webkit-appearance none

.ni-btn__container:hover:enabled
  color var(--txt, #333)
  text-decoration none
  border-color var(--bc, #ddd)
  background var(--app-fg, #eee)

.ni-btn__icon
  font-size 1em
  line-height 1

.ni-btn__icon + .ni-btn__value, .ni-btn__img + .ni-btn__value
  padding-left 0.375em

.ni-btn__img
  height 1.6em

.ni-btn__value
  line-height 1.5
  font-weight 300
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
  color var(--dim, #666) !important

  &:focus:enabled
    outline none

/* right aligned icons */
.ni-btn__container.ni-btn__icon-right
  flex-direction row-reverse

  .ni-btn__icon + .ni-btn__value
    padding-left 0
    padding-right 0.375em

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

.ni-btn__container.ni-btn--primary
  background var(--primary, #99f)
  border-color var(--primary-bc, #00f)
  .ni-btn__value
    color var(--bright, #000)

.ni-btn__container.ni-btn--success
  border-color var(--success-bc, #0f0)
  .ni-btn__value
    color var(--bright, #000)

.ni-btn__container.ni-btn--warning
  border-color var(--warning-bc, #f90)
  .ni-btn__value
    color var(--bright, #000)

.ni-btn__container.ni-btn--danger
  border-color var(--danger-bc, #f00)
  .ni-btn__value
    color var(--bright, #000)
</style>
