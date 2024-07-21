<template>
  <div>
    <button @click="fetchData">Fetch Data</button>
    <div v-if="data">
      <h3>API Data:</h3>
      <pre>{{ data }}</pre>
    </div>
  </div>
</template>

<script>
export default {
  name: 'FetchData',
  data() {
    return {
      data: null
    }
  },
  methods: {
    async fetchData() {
      try {
        const response = await fetch('http://http://localhost/mi%20sitio%20web/public/.com/')
        if (!response.ok) {
          throw new Error('HTTP error! status: ${response.status}')
        }
        const result = await response.json()
        this.data = result
      } catch (error) {
        console.error('Error fetching data:', error)
      }
    }
  }
}
</script>

<style scoped>
button {
  padding: 10px 20px;
  font-size: 16px;
}
.data {
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
