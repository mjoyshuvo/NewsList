<template>
  <div class="sourceselection">
    <div>
      <div class="jumbotron">
        <h2><i class="far fa-newspaper"></i>&nbsp;News List</h2>
        <h4>Select News Source</h4><br>
        <select class="form-control" v-on:change="sourceChanged">
          <option value="">Please select news source ...</option>
          <option v-for="source in sources" v-bind:value="source.id">{{source.name}}</option>
        </select><br>
        <div v-if="source">
          <h6>{{source.description}}</h6>
          <a v-bind:href="source.url" class="btn btn-outline-info" target="_blank">Go To {{source.name}} Website</a>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: 'sourceselection',
  data () {
    return {
      sources: [],
      source: ''
    }
  },
  methods: {
    sourceChanged: function(e) {
     for (var i=0; i<this.sources.length; i++) {
       if (this.sources[i].id == e.target.value) {
         this.source = this.sources[i];
       }
     }
     this.$emit('sourceChanged', e.target.value);
    }
  },
  created: function () {
    axios.get('https://newsapi.org/v1/sources?language=en&apiKey=0753f130598040e88c087c1b2169af44')
      .then(response => {
        this.sources = response.data.sources;
      });
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>