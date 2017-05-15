<template>
  <a class="ni-btn" v-if="type === 'anchor'">
    <span :class="btnClass">
      <i v-if="icon" :class="'ni-btn-icon fa fa-' + icon" aria-hidden="true"></i>
      <span class="ni-btn-value" v-if="value">{{ value }}</span>
    </span>
  </a>
  <router-link class="ni-btn" v-else-if="type === 'router-link'">
    <span :class="btnClass">
      <i v-if="icon" :class="'ni-btn-icon fa fa-' + icon" aria-hidden="true"></i>
      <span class="ni-btn-value" v-if="value">{{ value }}</span>
    </span>
  </router-link>
  <button class="ni-btn" :type="btnType" v-else>
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
      let value = 'ni-btn-container'
      if (this.iconPos) value += ` ni-btn-icon-${this.iconPos}`
      if (this.size) value += ` ni-btn-size-${this.size}`
      if (this.theme) value += ` ni-btn-theme-${this.theme}`
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
