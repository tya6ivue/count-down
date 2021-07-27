<template>
  <div class="main">
    <div>
      <div>
        <h2>{{ title }}</h2>

        <div id="timer" class="timer">
          <span id="minutes">{{ minutes }}</span>
          <span id="middle">:</span>
          <span id="seconds">{{ seconds }}</span>
        </div>

        <div>
          <button id="start" class="button" v-if="!timer" @click="startTimer">
            start
          </button>
          <button id="stop" class="button" v-if="timer" @click="stopTimer">
            Stop
          </button>

          <button
            id="reset"
            class="button"
            v-if="resetButton"
            @click="resetTimer"
          >
            resetTimer
          </button>
        </div>
      </div>
    </div>
  </div>
</template>



<script>
export default {
  name: "abc",

  data() {
    return {
      timer: null,
      totalTime: 25 * 60,
      resetButton: false,
      title: "Let the countdown begin!!",
    };
  },

  methods: {
    startTimer: function () {
      this.timer = setInterval(() => this.countdown(), 1000);
      this.resetButton = true;
      this.title = "Greatness is within sight!!";
    },
    stopTimer: function () {
      clearInterval(this.timer);
      this.timer = null;
      this.resetButton = true;
      this.title = "Never quit, keep going!!";
    },
    resetTimer: function () {
      this.totalTime = 25 * 60;
      clearInterval(this.timer);
      this.timer = null;
      this.resetButton = false;
      this.title = "Let the countdown begin!!";
    },
    padTime: function (time) {
      return (time < 10 ? "0" : "") + time;
    },
    countdown: function () {
      if (this.totalTime >= 1) {
        this.totalTime--;
      } else {
        this.totalTime = 0;
        this.resetTimer();
      }
    },
  },

  computed: {
    minutes: function () {
      const minutes = Math.floor(this.totalTime / 60);
      return this.padTime(minutes);
    },
    seconds: function () {
      const seconds = this.totalTime - this.minutes * 60;
      return this.padTime(seconds);
    },
  },
};
</script>

<style scoped>
.button {
  width: 100px;
  color: red;
  border-radius: 7px;
  height: 30px;
  font-size: 15px;
  background-color: rgb(73, 73, 204);
}
.timer {
  width: 200px;
  border-radius: 10px;
  padding-top: 50px;
  font-size: 20px;
  text-align: center;
  border: 2px solid;
  height: 100px;
  margin-bottom: 20px;
}
.main {
  margin-left: 45%;
}
</style>