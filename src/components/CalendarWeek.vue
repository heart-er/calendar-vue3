<template>
  <div id="calendar-week" class="container">
    <div class="columns is-mobile">
      <CalendarDay
        v-for="day in sharedState.state.seedData"
        :key="day.id"
        :day="day"
      />
    </div>
  </div>
</template>

<script>
import { store } from '../store.js';
import CalendarDay from './CalendarDay.vue';
import { reactive } from '@vue/composition-api';

export default {
  name: 'CalendarWeek',
  setup() {
    const sharedState = reactive({
      state: store.state
    });
    return {
      sharedState
    };
  },
  components: {
    CalendarDay
  }
};
</script>

<style lang="scss" scoped>
#calendar-week {
  margin-bottom: 50px;
  .column {
    padding: 0 0 0 0;
  }
}
</style>
