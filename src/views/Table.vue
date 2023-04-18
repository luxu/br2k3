<template>
  <div id="app">
    <h1>Vue Scroll Table</h1>
    <scroll-table>
      <template>
          Primeiro
      </template>
      <template>
          Segundo
      </template>
    </scroll-table>
  </div>
</template>

<script>
  import ScrollTable from "vue-scroll-table"

  const getData = () => {
    // Or load your own data.
    return fetch(
      'https://raw.githubusercontent.com/stijlbreuk/vue-scroll-table/master/example/assets/data.json'
    );
  };

  export default {
    name: 'App',
    components: {
      ScrollTable
    }
  }
</script>
