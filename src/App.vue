<script>

export default {
  created() {
    this.startTimer();
  },
  data() {
    return {
      info: null
    }
  },
  methods: {
    getTimezone() {
       fetch('http://worldtimeapi.org/api/timezone/Asia/Ho_Chi_Minh')
      .then(response => response.json())
      .then(data => {
        this.info = data})
    },
    startTimer() {
        clearInterval(this.interval)
        let interval = setInterval(() => {
          this.getTimezone();
        }, 1000)
    },
  },
  mounted () {
  }
}
</script>

<template>
  <h1>Asia/Ho_Chi_Minh Time..</h1>
  <br/>
  <ul>
    <li v-for="(value, key) in info">
      {{ key }}: {{ value }}
    </li>
  </ul>
</template>