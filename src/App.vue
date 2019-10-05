<template>
  <div id="app">
    <calendar-week></calendar-week>
    <calendar-entry></calendar-entry>
  </div>
</template>

<script>
import CalendarWeek from './components/CalendarWeek';
import CalendarEntry from './components/CalendarEntry';

export default {
  name: 'app',
  components: {
    CalendarWeek,
    CalendarEntry
  }
};
</script>

<style lang="scss">
body,
html {
  height: 100%;
}
#app {
  height: inherit;
  background: #6e6e6e;
  display: flex;
  flex-direction: column;
  align-items: center;
  -webkit-align-items: center;
  justify-content: center;
  -webkit-justify-content: center;
}
</style>
