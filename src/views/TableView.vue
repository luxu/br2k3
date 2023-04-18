<template>
  <div>
    <form id="search">
      <input name="query" v-model="searchQuery">
    </form>
    <DemoGrid
      :data="gridData"
      :columns="gridColumns"
      :filter-key="searchQuery">
    </DemoGrid>
  </div>
</template>

<script>
import DemoGrid from './Grid.vue'

const API_URL = `http://localhost:5173`

export default {
    components: {
      DemoGrid
    },
    data: () => ({
      searchQuery: '',
      gridColumns: ['id', 'nome', 'escudo'],
      gridData: [],
      url: API_URL
    }),
    methods: {
        async loadTimes() {
            const url = `${this.url}/times.json`
            fetch(url)
            .then((response) => {
              response.json()
                  .then((times) => {
                    times.map(infos => {
                        console.log(infos)
                        this.gridData.push(infos)
                    })
              })
            }).catch((error) => {
                console.log(error)
            })
        }
    },
    created() {
        this.loadTimes()
    }
}
</script>
