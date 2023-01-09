<template>
  <v-app>
    <app_header v-bind:chartType.sync="chartType"/>

    <v-main>
      <keep-alive>
        <component v-bind:is="chartType"></component>
      </keep-alive>
    </v-main>
  </v-app>
</template>

<script>
import app_header from './components/header';
import app_monthtable from './components/tables/monthtable';
import app_weektable from './components/tables/weektable';
import app_daytable from './components/tables/daytable';

export default {
  name: 'App',

  components: {
    app_header,
    app_monthtable,
    app_weektable,
    app_daytable,
  },

  data: () => ({
    chartType: 'app_monthtable'
  }),
};
</script>
