<template>
  <div class="example_bar_graph">
    <h1>{{ msg }}</h1>
    <h1>This is an example bar graph page.</h1>
    <ul class="graph_stats">
      <li>maxBarHeight: {{ maxBarHeight.toFixed(2) }}</li>
      <li>qtyBars: {{ qtyBars }}</li>
    </ul>
    <div class="graph">
      <div class="bar" v-bind:title="bar.y" v-for="bar in fitDataToGraph()" v-bind:key="bar.x" v-bind:style="{ bottomMargin: 0, left: ((bar.x - 1) * bar.sw) + '%', height: bar.sy + '%', width: bar.sw + '%', backgroundColor: bar.sc }">
        <div class="bar_label">{{ bar.y.toFixed(2) }}</div>
      </div>
    </div>
    <button v-on:click="updateBars">updateBars (w/ random values)</button>
  </div>
</template>

<script>
export default {
  props: {
    msg: String
  },
  methods: {
    rgb: function(r,g,b) {
      return "rgb("+r+","+g+","+b+")";
    },
    fitBarToGraph: function(bar) {
      var sy = 100 * bar.y / this.maxBarHeight;
      var sc = this.rgb(sy * 2,sy * 2,sy * 2);
      return {x: bar.x, y: bar.y, sw: (100 / this.qtyBars), sy: sy, sc: sc};
    },
    fitDataToGraph: function () {
      var orig = this.graph.bars;
      this.qtyBars = orig.length;
      this.maxBarHeight = Math.max.apply(null,
                        Object.keys(orig).map(function(e) {
                                return orig[e]['y'];
                        }));
      return orig.map(this.fitBarToGraph);
    },
    randomBars: function() {
      return [
          {x: 1, y: Math.random()},
          {x: 2, y: Math.random()},
          {x: 3, y: Math.random()},
          {x: 4, y: Math.random()},
          {x: 5, y: Math.random()},
          {x: 6, y: Math.random()},
          {x: 7, y: Math.random()},
          {x: 8, y: Math.random()},
          {x: 9, y: Math.random()},
          {x: 10, y: Math.random()},
          {x: 11, y: Math.random()},
          {x: 12, y: Math.random()},
          {x: 13, y: Math.random()},
          {x: 14, y: Math.random()},
          {x: 15, y: Math.random()},
        ];
    },
    updateBar: function(bar) {
      this.$set(this.graph.bars, bar.x - 1, bar);
    },
    updateBars: function() {
      var me = this;
      var newData = this.randomBars(); // In a real app, this might set newData based on a response from an API call.
      newData.forEach(function(bar) {
        me.updateBar(bar);
      });
    }
  },
  data: function () {
    return {
      maxBarHeight: 100,
      qtyBars: 100,
      graph: {
        label: 'some graph',
        bars: this.randomBars()
      }
    }
  },
}
</script>

<style lang="scss">
.example_bar_graph {
  color: blue;

  .graph {
    position: relative;
    width: 100%;
    height: 100px;
    border: 0.1em solid gray;
    margin-top: 2em;
    margin-bottom: 1em;
  }

  .bar {
    position: absolute;
    // width: 9.5%;
    outline: 0.1em solid lightgray;
    bottom: 0;
    background-color: yellow;
    text-align: center;
  }

  .bar_label {
    position: relative;
    // width: 9.5%;
    // outline: 0.1em solid lightgray;
    top: -1.5em;
    // background-color: yellow;
  }
}
</style>
