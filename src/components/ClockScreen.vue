<template>
  <div class="container">
    <div class="clock">
      <div class="date">
        <p>{{ year }}/{{ month }}/{{ day }}</p>
      </div>
      <div class="time">
        <p>
          {{ hours }}:{{ minutes }}<span class="seconds">:{{ seconds }}</span>
        </p>
      </div>
      <div class="button" v-on:click="showMessage()">
        <p>10秒後にアラームを設定</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ClockScreen",
  data() {
    return{
      date: new Date(),
    };
  },
  computed: {
    year() {
      return this.date.getFullYear();
    },
    month() {
      return this.date.getMonth() + 1;
    },
    day() {
      return this.dateTimePadding(this.date.getDate());
    },
    hours() {
      return this.dateTimePadding(this.date.getHours());
    },
    minutes() {
      return this.dateTimePadding(this.date.getMinutes());
    },
    seconds() {
      return this.dateTimePadding(this.date.getSeconds());
    },
  },
  mounted() {
    this.setDate();
    setInterval(() => this.setDate(), 1000);
  },
  methods: {
    dateTimePadding(num) {
      return ("0" + num).slice(-2);
    },
    setDate() {
      this.date = new Date();
    },
    showMessage() {
      window.setTimeout(() => {
        alert("10秒経過しました");
      }, 10000);
    },
  },
};
</script>

<style scoped>
.container {
  height: 100%;
  display: flex;
  flex-flow: column;
  justify-content: center;
  align-items: center;
  background-color: #262626;
}

p {
  margin: 0px;
}

.date,
.time {
  font-weight: 700;
  color: #00ff01;
}

.date {
  font-size: 16px;
  text-align: right;
}

.time {
  font-size: 70px;
}

.seconds {
  font-size: 30px;
}

.button {
  border: 1px solid #fcfcfc;
  text-align: center;
  padding: 10px 0;
  color: #fcfcfc;
  cursor: pointer;
}
</style>