<template>
  <div>
    <h1>
      Vue app
      <SearchBar @termChange="onTermChange"></SearchBar>
    </h1>
  </div>
</template>

<script>
import SearchBar from './components/SearchBar';
export default {
  name: 'App',
  components: {
    SearchBar
  },
  methods: {
    onTermChange(searchTerm) {
      console.log(searchTerm);
    }
  }
};
</script>
