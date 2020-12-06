<template>
  <div class="hello">
    <h1 class="title has-text-weight-bold">{{ msg }}</h1>

    <section class="section">
      <div class="container">
        <div class="columns">
          <input type="text" class="input" v-model="commit" placeholder="enter your parameter" />
          <h2>{{}}</h2>
          <ul class="card">
            <li v-for="rep in reps" :key="rep.message">{{rep}}</li>
          </ul>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
function apiReq() {
  return fetch(
    `https://api.github.com/repos/bohorquez866/githhub-commit-list/commits/`
  ).then(response => response.json());
}

export default {
  name: "home",
  props: {
    msg: String
  },

  data: function() {
    return {
      commit: "",
      reps: []
    };
  },

  watch: {
    commit: function(val, oldVal) {
      this.commit = val;
      apiReq(this.commit).then(console.log());
      console.log(oldVal);
    }
  }
};
</script>

<style scoped>
</style>
