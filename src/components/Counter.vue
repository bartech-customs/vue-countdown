<template>
  <div class="container mx-auto">
    <section class="text-2xl flex justify-center mb-4">
      <p>Counter</p>
    </section>
    <section class="flex justify-center text-2xl my-4">
      <p>{{ feedback }}</p>
    </section>
    <section
      v-if="loaded"
      class="flex  justify-center content-center text-center w-full text-gray-100 "
    >
      <div class="days mt-1">
        <div class="w-full dispalyText">{{ days }}</div>
        <div class="label text-sm ">day</div>
      </div>
      <span class=" mx-2 dispalyText">:</span>
      <div class="days mt-1">
        <div class="flex flex-col dispalyText">{{ hours }}</div>
        <div class="label text-sm">hour</div>
      </div>
      <span class=" dispalyText mx-2">:</span>
      <div class="days mt-1">
        <div class="flex flex-col dispalyText ">{{ mins }}</div>
        <div class="label text-sm">min</div>
      </div>
      <span class=" dispalyText mx-2 ">:</span>
      <div class="days mt-1">
        <div class="w-40 seconds dispalyText">
          {{ seconds }}
        </div>
        <div class="label  text-sm">sec</div>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  props: ["year", "month", "date", "hour", "min", "sec", "ms"],
  data() {
    return {
      days: 0,
      hours: 0,
      mins: 0,
      seconds: 0,
      loaded: false,
      feedback: null,
    };
  },

  computed: {
    _seconds() {
      return 1000;
    },
    _minutes() {
      return this._seconds * 60;
    },
    _hours() {
      return this._minutes * 60;
    },
    _days() {
      return this._hours * 24;
    },
    endDate() {
      return new Date(
        this.year,
        this.month,
        this.date,
        this.hour,
        this.min,
        this.sec,
        this.ms
      );
    },
  },
  methods: {
    showRemaining() {
      const timer = setInterval(() => {
        const now = new Date();

        const distance = this.endDate.getTime() - now.getTime();

        if (distance < 0) {
          clearInterval(timer);
          this.feedback = "Time is over";
          this.loaded = true;

          return;
        }

        const days = Math.floor(distance / this._days);
        const hours = Math.floor((distance % this._days) / this._hours);
        const minutes = Math.floor((distance % this._hours) / this._minutes);
        const seconds = Math.floor((distance % this._minutes) / this._seconds);
        this.days = days < 10 ? "0" + days : days;
        this.hours = hours < 10 ? "0" + hours : hours;
        this.mins = minutes < 10 ? "0" + minutes : minutes;
        this.seconds = seconds < 10 ? "0" + seconds : seconds;
        this.feedback = "Remaining";
        this.loaded = true;
      }, 1000);
    },
  },
  mounted() {
    this.showRemaining();
  },
};
</script>
<style scoped>
.seconds {
  display: block;
}
.dispalyText {
  text-shadow: -8px -8px 12px rgba(255, 255, 255, 0.4),
    8px 8px 12px rgba(0, 0, 0, 0.08);
  caret-color: #262626;
  outline: none;
  font-size: 15rem;
}
</style>
