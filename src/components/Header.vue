<template>
  <div class="my-20 w-20 text-cyan-text">
    <IconLogo />
  </div>
</template>

<script>
import IconLogo from "./Icons/Logo.vue"

export default {
  name: 'Header',
  props: {
  },
  components: {
    IconLogo
  }
}
</script>
