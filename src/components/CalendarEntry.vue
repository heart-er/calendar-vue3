<template>
  <div id="calendar-entry">
    <div class="calendar-entry-note">
      <input type="text" placeholder="add plan" v-model="inputEntry" required />
      <p class="calendar-entry-day">
        Day of event: <span class="bold">{{ titleOfActiveDay }}</span>
      </p>
      <a
        class="button is-primary is-small is-outlined "
        @click="submitEvent(inputEntry)"
      >
        Submit
      </a>
    </div>
    <p style="color: red; font-size: 13px" v-if="error">
      You must type something first!
    </p>
  </div>
</template>

<script>
import { store } from '../store.js';
import { ref, computed } from '@vue/composition-api';

export default {
  name: 'CalendarEntry',
  setup() {
    let inputEntry = ref('');
    let error = ref(false);

    let titleOfActiveDay = computed(() => store.getActiveDay().fullTitle);

    const submitEvent = eventDetails => {
      if (eventDetails === '') return (error.value = true);

      store.submitEvent(eventDetails);
      inputEntry.value = '';
      error.value = false;
    };

    return {
      inputEntry,
      error,
      titleOfActiveDay,
      submitEvent
    };
  }
};
</script>

<style lang="scss" scoped>
#calendar-entry {
  background: #fff;
  border: 1px solid #42b883;
  border-radius: 10px;
  max-width: 300px;
  margin: 0 auto;
  padding: 20px;

  .calendar-entry-note {
    display: flex;
    flex-direction: column;
    justify-content: center;
    input {
      width: 200px;
      font-weight: 600;
      border: 0;
      border-bottom: 1px solid #ccc;
      font-size: 15px;
      height: 30px;
      margin-bottom: 10px;

      &:focus {
        outline: none;
      }
    }

    .calendar-entry-day {
      color: #42b883;
      font-size: 12px;
      margin-bottom: 10px;
      padding-bottom: 5px;

      .bold {
        font-weight: 600;
      }
    }

    .submit {
      display: block;
      margin: 0 auto;
    }
  }
}
</style>
