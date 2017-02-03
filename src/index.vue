<template>
  <button class="pz-btn-wrapper" :type="btnType">
    <span :class="btnClass">
      <i v-if="btnIcon" :class="'pz-btn-icon fa fa-' + btnIcon" aria-hidden="true"></i>
      <span class="pz-btn-value" v-if="value">{{ value }}</span>
    </span>
  </button> 
</template>

<script>
export default {
  name: 'pz-btn',
  computed: {
    btnClass () {
      let value = 'pz-btn'
      if (this.IconPos === 'right') value += ' pz-btn-icon-right'
      if (this.size === 'large') value += ' pz-btn-large'
      if (this.size === 'small') value += ' pz-btn-small'
      if (this.theme === 'alpha-black') value += ' pz-theme-alpha-black'
      if (this.theme === 'tendermint') value += ' pz-theme-tendermint'
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
