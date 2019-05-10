<template>
  <div class="example_misc_a">
    <h1>{{ msg }}</h1>
    <h1>This is an example_misc page</h1>
    <ul id="example-1">
      <li v-for="item in items" v-bind:key="item.id">
        {{ item.message }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: {
    msg: String
  },
  data: function () {
    return {
      items: [
        { id: 1, message: 'Foo '  + Math.random(10).toString()},
        { id: 2, message: 'Bar '  + new Date().toLocaleString() }
      ]
    }
  },
}
</script>

<style lang="scss">
.example_misc_a {
  color: blue;
}
</style>
