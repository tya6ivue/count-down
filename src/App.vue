<template>
  <div id="app">
    <div v-for="(len, index) in NoOfTimer" :key="index">
      <DisplayCmp />
    </div>
    <button class="button" @click="addTimer">Add more</button>
  </div>
</template>

<script>
import DisplayCmp from "./components/DisplayCmp.vue";
export default {
  name: "App",
  components: {
    DisplayCmp,
  },
  data() {
    return {
      NoOfTimer: [1],
    };
  },

  methods: {
    addTimer() {
      this.NoOfTimer.push(1);
    },
  },
};
</script>

<style scoped>
.button {
  margin-top: 20px;
  width: 200px;
  margin-left: 45%;
}
</style>>

