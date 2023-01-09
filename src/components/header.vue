<template>
  <v-app-bar app color="#a9a9a9" rounded='xl' height='100' class="mb-3">
    <v-row class="pt-5">
      <v-col cols='2'>
        <v-text-field
          dense
          outlined
        ></v-text-field>
      </v-col>
      <v-col cols='2'>
        <v-select
          dense
          outlined
          label='Тип графика'
          :items='chartTypes'
          item-text='text'
          item-value='value'
          v-model="selectedChartType"
          @change="changeChartType"
        ></v-select>
      </v-col>
      <v-col cols='2'>
        <v-select
          dense
          outlined
          label='фильтр по сотрудникам'
        ></v-select>
      </v-col>
      <v-col cols='2'>
        <v-select
          dense
          outlined
          label='фильтр по делам'
          :items='businessItemsForFilter'
          item-text='text'
          item-value='value'
          multiple
          v-model="businessItems"
        ></v-select>
      </v-col>
      <v-spacer></v-spacer>
      <v-col cols='2' class="pt-0">
        <v-btn block small class="mb-2">План сотрудников</v-btn>
        <v-btn block small>мой план на месяц</v-btn>
      </v-col>
    </v-row>
  </v-app-bar>
</template>

<script>
export default {
  name: "app_header",
  data: ()=>({
    chartTypes: [
      {
        text: 'День',
        value: 'app_daytable'
      },
      {
        text: 'Неделя',
        value: 'app_weektable'
      },
      {
        text: 'Месяц',
        value: 'app_monthtable'
      },
    ],
    selectedChartType: 'app_monthtable',
    businessItemsForFilter: [
      {
        text: 'С командировками',
        value: 'businesstrips'
      },
      {
        text: 'Показать дни без дел',
        value: 'free'
      },
      {
        text: 'Только командировки',
        value: 'businesstripsOnly'
      },
      {
        text: 'Только дни с делами',
        value: 'busy'
      },
    ],
    businessItems: []
  }),
  methods:{
    changeChartType(val){
      this.$emit('update:chartType', val);
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped></style>
