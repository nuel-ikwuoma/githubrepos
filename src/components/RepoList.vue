<template>
  <div id="repo-container">
    <h2 v-if="!repos || repos.length == 0">No repository for this user</h2>
    <ul v-else>
      <h2 class="list-head">Available public repositories</h2>
      <li class="list" v-for="repo in repos" v-bind:key="repo.id">
        <span class="repo-text">{{ repo.name }}</span>&nbsp;
        <a :href="repo.html_url" target="_blank" rel="noopener">
            <span class="repo-description">{{ repo.description }}</span>
        </a>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'RepoList',
  props: {
    repos: Array,
  },
};
</script>

<style scoped>
#repo-container {
  width: 70%;
  margin: 50px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.3);
  overflow: scroll;
}
h2 {
  font-size: 22px;
  text-align: center;
  color: #173953;
  text-transform: capitalize;
}

.repo-text {
  font-weight: 400;
  color: #141414;
  font-family: "Lucida Console", "Courier New", monospace;
}
.repo-description {
  font-weight: 600;
  font-style: bold;
  color: #2a6592;
}

ul li {
    padding: 4px;
    list-style: square;
}

a {
    text-decoration: none;
}

a:hover {
  text-decoration: underline;
}

a:active {
  color: black;
}

.footer {
  font-size: 15px;
  font-weight: 600;
}

.list-head {
    text-transform: capitalize;
}

@media screen and (max-width: 600px) {
  #repo-container {
    width: 100%;
    margin: 0;
    box-shadow: none;
  }
}
</style>
