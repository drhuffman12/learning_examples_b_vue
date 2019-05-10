<template>
  <div class="example_misc">
    <ExampleMiscA msg="Welcome to ExampleMiscA"/>
  </div>
</template>

<script>
import ExampleMiscA from '@/components/ExampleMiscA.vue'

export default {
  name: 'example_misc',
  data: function () {
    return {
      items: [
        { id: 1, message: 'Foo '  + Math.random(10).toString()},
        { id: 2, message: 'Bar '  + new Date().toLocaleString() }
      ]
    }
  },
  components: {
    ExampleMiscA
  }
}
</script>

<style lang="scss">
.example_misc {
  text-align: left;
}
</style>
