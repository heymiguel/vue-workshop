<template>
  <div id="app" class="wrapper">
    <Search
      @handleFlags="handleFlags($event)"
      @handleChange="handleChange($event)"
      @resetSearch="resetSearch"
      :selectedSearchMethod="selectedSearchMethod"
    />
    <Results :repos='repos'/>
    <Searching :flags='flags'/>
    <Errors :flags='flags'/>
  </div>
</template>

<script>
import Search from '@/components/Search';
import Results from '@/components/Results';
import Searching from '@/components/Searching';
import Errors from '@/components/Errors';

export default {
  name: 'App',
  components: {
    Search,
    Results,
    Searching,
    Errors,
  },
  data() {
    return {
      selectedSearchMethod: 'repo',
      repos: [],
      flags: {
        searching: false,
        errorHandling: false,
      },
    };
  },
  methods: {
    handleFlags(event) {
      this.flags[event.key] = event.val;
    },
    resetSearch() {
      this.flags.errorHandling = false;
      this.repos = [];
    },
    handleChange(event) {
      this[event.key] = event.val;
    },
  },
};
</script>

<style>
@import '../../sharedAssets/styles/style.css';

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
