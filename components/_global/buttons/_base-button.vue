<template>
  <button
    :disabled="loading"
    :tyoe="nativeType"
    class="btn"
    :class="{
      [`btn-${type}`]: true,
      ['btn-block']: block,
      [`btn-${size}`]: true
    }"
  >
    <span v-if="loading">
      <i class="fas fa-spinner fa-spin"></i>
    </span>
    <slot />
  </button>
</template>

<script>
  export default {
    props: {
      type: {
        type: String,
        default: 'primary'
      },
      nativeType: {
        type: String,
        default: '送信'
      },
      loading: {
        type: Boolean,
        default: false
      },
      block: {
        type: Boolean,
        default: false
      },
      size: {
        type: String,
        default: 'md'
      }
    }
  }
</script>

<style scoped>

</style>
