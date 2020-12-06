<template>
  <div class="hello">
    <h1 class="title has-text-weight-bold has-text-primary">{{ msg }}</h1>

    <section class="section">
      <div class="container">
        <div class>

                <ul class="cards is-flex is-justify-content-space-between columns is-variable is-3 is-multiline mt-6">
            <li
              class="card is-primary notification column is-one-third  mb-3 is-rounded"
              v-for="commit in commits"
              :key="commit"
            >
              <h2 class="has-text-weight-bold">
                Author
                <strong class="has-text-warning">{{commit.author.login}}</strong>
              </h2>
              <h3 class="has-text-weight-bold">
                <span>Sha:</span>
                <strong class="has-text-warning">{{commit.sha}}</strong>
              </h3>

              <h3 class="has-text-weight-semibold">
                Comment:
                <em v-if="commit.commit.message.length > 0">{{commit.commit.message}}</em>
              </h3>
              <p>
                <strong>Date:</strong>
                {{commit.commit.author.date}}
              </p>
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
      url: `https://api.github.com/search/commits?q=repo:bohorquez866/github-commit-list/master author-date:1973-01-01..2021-12-07`,
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
      })
        .then(response => response.json())
        .then(repos => {
          this.repos = repos;
          this.commits = repos.items;
          console.log(this.commits);
        })
        .catch(err => console.warn(err));
    }
  },

  beforeMount() {
    this.request();
  }
};
</script>

