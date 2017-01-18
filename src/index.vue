<template>
  <button :class="btnClass" :type="type">
    <i v-if="btnIcon" :class="'fa fa-' + btnIcon" aria-hidden="true"></i>
    <span class="value" v-if="btnValue">{{ btnValue }}</span>
  </button> 
</template>

<script>
export default {
  name: 'pz-button',
  computed: {
    btnClass () {
      let value = 'pz-button'
      if (this.btnSize === 'large') value += ' pz-button-large'
      if (this.btnSize === 'small') value += ' pz-button-small'
      return value
    },
    type () {
      if (this.btnType) return this.btnType
      else return 'submit'
    }
  },
  props: ['btn-value', 'btn-icon', 'btn-type', 'btn-size']
}
</script>

<style src="./style.css"></style>
