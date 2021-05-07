<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" />
    <h1>Cuenta regresiva</h1>
    <h3>
      {{ tiempo }}
    </h3>
    <button
      @click="cronos(btn.val)"
      v-for="(btn, index) in dataTime"
      :key="index"
      class="buton mx-4 mt-2 btn btn-danger"
    >
      {{ btn.min }}
    </button>
  </div>
</template>

<script>
export default {
  name: "App",

  data() {
    return {
      tiempo: "00:00",
      intervalo: "",
      dataTime: [
        {
          min: "3s",
          val: "3",
        },
        {
          min: "1m",
          val: "60",
        },
        {
          min: "5m",
          val: "300",
        },
        {
          min: "30m",
          val: "1800",
        },
      ],
    };
  },
  watch: {
    tiempo(v) {
      if (v === 0) this.parar();
    },
  },
  methods: {
    cronos(v) {
      this.tiempo = v;

      this.intervalo = setInterval(() => {
        this.tiempo--;
        // let minute = Math.floor((v / 60) % 60);
        // minute = (minute < 10)? 0 + minute : minute;
        // let seconds = v % 60;
        // seconds = (seconds < 10)? 0 + seconds : seconds;
        // console.log(minute);
        // console.log(seconds);
        // this.tiempo = minute + ":" + seconds;
        // console.log(this.tiempo);
      }, 1000);
    },
    parar() {
      clearInterval(this.intervalo);
      this.tiempo = "00:00";
    },
  },
};
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
