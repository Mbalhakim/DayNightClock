<template>
  <div class="clock" :style="clockStyle">
    <div class="hour-hand" :style="hourHandStyle"></div>
    <div class="minute-hand" :style="minuteHandStyle"></div>
    <div class="second-hand" :style="secondHandStyle"></div>
    
  </div>
</template>

<script>
export default {
  data() {
    return {
   
      clockStyle: {},
      hourHandStyle: {},
      minuteHandStyle: {},
      secondHandStyle: {}
    };
  },
  mounted() {
    this.updateClock();
    setInterval(this.updateClock, 1000);
  },
  methods: {
    updateClock() {
      const now = new Date();
      const seconds = now.getSeconds();
      const minutes = now.getMinutes();
      const hours = now.getHours();

      const rotateSeconds = 6 * seconds;
     
      const rotateMinutes = 6 * minutes;
      const rotateHours = 30 * (hours % 12) + minutes / 2;

      //  console.log("Time " + rotateHours + ":" + rotateMinutes + ":" + rotateSeconds)

      // this.clockStyle = {
      //   background: this.calculateBackgroundColor(hours)
      // };

      this.secondHandStyle = {
        transform: `rotate(${rotateSeconds}deg)`
      };

      this.minuteHandStyle = {
        transform: `rotate(${rotateMinutes}deg)`
      };

      this.hourHandStyle = {
        transform: `rotate(${rotateHours}deg)`
      };
    },
    calculateBackgroundColor(hours) {
      // Example calculation for background based on hour
      if (hours >= 6 && hours < 18) {
        // Daytime
        return "skyblue";
      } else {
        // Nighttime
        return "darkblue";
      }
    }
  }
};
</script>

<style>
body {
    background-color: rgb(33, 164, 127);
}
.clock {
  position: relative;
  width: 400px;
  height: 400px;
  background-image: url('~@/assets/clock-numbers.png');
  background-size: cover;
  background-color: white;
  background-repeat: no-repeat;
  border-radius: 50%;
}

.hour-hand,
.minute-hand,
.second-hand {
  position: absolute;
  left: 50%;
  top: 50%;
  transform-origin: bottom center;
}

.hour-hand {
  width: 6px;
  height: 96px;
  background: black;
  margin-left: -3px;
  margin-top: -96px;
  border-radius: 4px;
  transform-origin: 50% 95%;
  box-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3);
}

.minute-hand {
  width: 4px;
  height: 99px;
  background: black;
  margin-left: -2px;
  margin-top: -99px;
  border-radius: 4px;
  transform-origin: 50% 98%;
  box-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3);
}

.second-hand {
  width: 2px;
  height: 100px;
  background: red;
  margin-left: -1px;
  margin-top: -100px;
  border-radius: 2px;
  transform-origin: 50% 99%;
  box-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3);
}

</style>
