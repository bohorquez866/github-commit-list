<template>
  <div class="hello">
    <h1 class="title has-text-weight-bold">{{ msg }}</h1>

    <section class="section">
      <div class="container">
        <div class="columns">
          <input type="text" class="input" v-model="commit" placeholder="enter your parameter" />
          <ul class="card">
            <li v-for="rep in reps" :key="rep.message">{{rep}}</li>
          </ul>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
    msg: String,
  },

  data: function () {
    return {
      commit: "",
      reps: [],
    };
  },

  watch: {
    commit: function (val, oldVal) {
      this.commit = val;
      console.log(oldVal);
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
