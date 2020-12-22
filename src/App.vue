<template>
  <div id="app">
    <h1 class="app-title">Github repository list</h1>
    <RepoList :repos="repos" />
    <footer>
      <div className='footer'>
          Built with&nbsp;
          <span role='img' aria-label='love'>
            💚
          </span>&nbsp;
          by Emmanuel Ikwuoma
        </div>
    </footer>
  </div>
</template>

<script>
import axios from 'axios'
import RepoList from './components/RepoList.vue'

export default {
  name: 'App',
  data() {
    return {
      repos: null
    }
  },
  components: {
    RepoList
  },
  created() {
    const url = 'https://api.github.com/users/nuel-ikwuoma/repos'
    axios.get(url)
      .then(response => this.repos = response.data)
      .catch(console.error)
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  box-sizing: border-box;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  font-family: 'Amiri', serif;
  overflow: hidden;
}

h1 {
  text-transform: capitalize;
}
</style>
