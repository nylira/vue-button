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

<style src="./style.css"></style>
