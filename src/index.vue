<template>
  <a class="ni-btn-wrapper" v-if="btnType === 'anchor'">
    <span :class="btnClass">
      <i v-if="icon" :class="'ni-btn-icon fa fa-' + icon" aria-hidden="true"></i>
      <span class="ni-btn-value" v-if="value">{{ value }}</span>
    </span>
  </a>
  <router-link class="ni-btn-wrapper" v-else-if="btnType === 'router-link'">
    <span :class="btnClass">
      <i v-if="icon" :class="'ni-btn-icon fa fa-' + icon" aria-hidden="true"></i>
      <span class="ni-btn-value" v-if="value">{{ value }}</span>
    </span>
  </router-link>
  <button class="ni-btn-wrapper" :type="btnType" v-else>
    <span :class="btnClass">
      <i v-if="icon" :class="'ni-btn-icon fa fa-' + icon" aria-hidden="true"></i>
      <span class="ni-btn-value" v-if="value">{{ value }}</span>
    </span>
  </button> 
</template>

<script>
export default {
  name: 'ni-btn',
  computed: {
    btnClass () {
      let value = 'ni-btn'
      if (this.iconPos === 'right') value += ' ni-btn-icon-right'
      if (this.size === 'lg') value += ' ni-btn-large'
      if (this.size === 'sm') value += ' ni-btn-small'
      if (this.theme === 'alpha-black') value += ' ni-theme-alpha-black'
      if (this.theme === 'tendermint') value += ' ni-theme-tendermint'
      return value
    },
    btnType () {
      if (this.type) return this.type
      else return 'button'
    }
  },
  props: ['value', 'icon', 'icon-pos', 'type', 'size', 'theme']
}
</script>

<style src="./style.css"></style>
