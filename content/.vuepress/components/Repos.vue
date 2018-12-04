<template>
  <div>
    <h2>Repositories</h2>
    <ul>
      <li v-for="repo in repos" :key="repo.title">
        <img :src="'repos/' + repo.logo" alt="repo.title" width="100">
        <br>
        <a :href="repo.url" target="_blank">{{repo.title}}:</a>
        {{repo.description}}
      </li>
    </ul>
  </div>
</template>

<script>
import repos from "../public/repos/repositories.json";

export default {
  data() {
    return {
      repos
    };
  }
};
</script>
