<template>
  <div>
    <h2>
      Settings
    </h2>

    <div class="form flex mt-10  md:flex-row">
      <div class="form-element  mr-1">
        <div>
          <label for="year" class="block text-sm font-medium text-gray-700">
            Year
          </label>
          <div class="mt-1">
            <input
              type="number"
              min="2020"
              id="year"
              class="shadow block w-full p-2
            text-lg  text-center  bg-transparent
            border border-transparent focus:outline-none focus:ring-1 focus:ring-gray-400 focus:border-transparent rounded"
              v-model="newYear"
              @change="$emit('update:year', newYear)"
            />
          </div>
        </div>
      </div>
      <div class="form-element mr-1">
        <div>
          <label
            for="month"
            class="block text-sm flex-1 font-medium text-gray-700"
          >
            Month
          </label>
          <div class="mt-1">
            <input
              type="number"
              min="0"
              max="12"
              id="month"
              class="shadow block w-full p-2
            text-lg  text-center  bg-transparent 
            border border-transparent focus:outline-none focus:ring-1 focus:ring-gray-400 focus:border-transparent rounded"
              v-model="newMonth"
              @change="$emit('update:month', newMonth)"
            />
          </div>
        </div>
      </div>
      <div class="form-element mr-1">
        <div>
          <label for="date" class="block text-sm font-medium text-gray-700">
            Date
          </label>
          <div class="mt-1">
            <input
              type="number"
              min="0"
              max="31"
              id="date"
              class="shadow block w-full p-2
            text-lg  text-center  bg-transparent 
            border border-transparent focus:outline-none focus:ring-1 focus:ring-gray-400 focus:border-transparent rounded"
              v-model="newDate"
              @change="$emit('update:date', newDate)"
            />
          </div>
        </div>
      </div>
      <div class="form-element mr-1">
        <div>
          <label for="hour" class="block text-sm font-medium text-gray-700">
            Hour
          </label>
          <div class="mt-1">
            <input
              type="number"
              min="0"
              max="24"
              id="hour"
              class="shadow block w-full p-2
            text-lg  text-center  bg-transparent
            border border-transparent focus:outline-none focus:ring-1 focus:ring-gray-400 focus:border-transparent rounded"
              v-model="newHour"
              @change="$emit('update:hour', newHour)"
            />
          </div>
        </div>
      </div>
      <div class="form-element mr-1">
        <div>
          <label for="min" class="block text-sm font-medium text-gray-700">
            Minutes
          </label>
          <div class="mt-1">
            <input
              type="number"
              min="0"
              max="60"
              id="min"
              class="shadow block w-full p-2
            text-lg  text-center  bg-transparent
            border border-transparent focus:outline-none focus:ring-1 focus:ring-gray-400 focus:border-transparent rounded"
              v-model="newMin"
              @change="$emit('update:min', newMin)"
            />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["year", "month", "date", "hour", "min", "sec", "ms"],
  data() {
    return {
      newYear: this.year,
      newMonth: this.month,
      newDate: this.date,
      newHour: this.hour,
      newMin: this.min,
    };
  },
  watch: {},
};
</script>

<style scoped></style>
