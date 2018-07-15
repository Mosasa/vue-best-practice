<template>
  <div>
    Main
    <click-component v-for="i in 5" :key="i" :index="i" />
    <show-component></show-component>
  </div>
</template>

<script>
import clickComponent from '@/components/clickComponent'
import showComponent from '@/components/showComponent'
export default {
  components: {
    clickComponent,
    showComponent
  }
}
</script>

<style>

</style>
