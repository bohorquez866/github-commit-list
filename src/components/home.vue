<template>
  <div class="hello">
    <h1 class="title has-text-weight-bold">{{ msg }}</h1>

    <section class="section">
      <div class="container">
        <div class>
          <h2>{{}}</h2>
          <ul class="cards columns is is-multiline mt-6">
            <li class="card column is-half mb-3" v-for="commit in commits" :key="commit.items">
              <h3 class="has-text-weight-bold">
                Owner:
                <strong class="has-text-link">{{commit}}</strong>
              </h3>
              <p>sha: {{commit.id}}</p>
              <p>comment: {{commit.description}}</p>
            </li>
          </ul>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  name: "home",
  props: {
    msg: String
  },

  data: function() {
    return {
      url: `https://api.github.com/search/commits?q=repo:bohorquez866/github-commit-list author-date:2020-01-01..2020-12-07`,
      commits: {},
      res: [],
      index: 0
    };
  },
  methods: {
    request() {
      return fetch(this.url, {
        method: "GET",
        headers: {
          Accept: "application/vnd.github.cloak-preview"
        }
        //        Authorization: `d5a9b2b60eb551ad9313360efdf6018406c8e15a`
      })
        .then(response => response.json())
        .then(repos => {
          this.repos = repos;
          console.log(repos);
          this.commits = repos;
        })
        .catch(err => console.warn(err));
    }
  },
  beforeMount() {
    this.request();
  }
};
</script>

