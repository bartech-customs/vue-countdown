<template>
  <div class="home bg-gray-100">
    <Counter
      :year="year"
      :month="month"
      :date="date"
      :hour="hour"
      :min="min"
      :sec="sec"
      :ms="ms"
    />

    <Settings
      :year.sync="year"
      :month.sync="month"
      :date.sync="date"
      :hour.sync="hour"
      :min.sync="min"
      :sec="sec"
      :ms="ms"
      class="my-12 container mx-auto"
    />
  </div>
</template>

<script>
// @ is an alias to /src
import Counter from "@/components/Counter.vue";
import Settings from "@/components/Settings.vue";
export default {
  name: "Home",
  data() {
    return {
      year: 2021,
      month: 2,
      date: 5,
      hour: 0,
      min: 0,
      sec: 10,
      ms: 10,
    };
  },
  components: {
    Counter,
    Settings,
  },
};
</script>
