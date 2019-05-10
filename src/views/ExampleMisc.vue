<template>
  <div class="example_misc">
    <ExampleBarGraph msg="Welcome to ExampleBarGraph"/>
  </div>
</template>

<script>
import ExampleBarGraph from '@/components/ExampleBarGraph.vue'

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
    ExampleBarGraph
  }
}
</script>

<style lang="scss">
.example_misc {
  text-align: left;
}
</style>
