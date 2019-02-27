<template>
<v-data-table
    :headers="headers"
    :items="desserts"
    :pagination.sync="pagination"
    class="elevation-1"
  >
    <template slot="items" slot-scope="props">
      <td class="text-xs-left">{{ props.item.name }}</td>
      <td class="text-xs-left">{{ props.item.calories }}</td>
      <td class="text-xs-left">{{ props.item.fat }}</td>
      <td class="text-xs-left">{{ props.item.carbs }}</td>
      <td class="text-xs-left">{{ props.item.protein }}</td>
      <td class="text-xs-left">{{ props.item.iron }}</td>
      <td class="text-xs-left">
        <v-btn  color="red"></v-btn>
      </td>
    </template>
  </v-data-table>
</template>

<script>
// eslint-disable-next-line
/* eslint-disable */
import axios from 'axios';
  export default {
    data() {
    return {
      pagination: {
        rowsPerPage: -1
      },
      headers: [
          {
            text: 'Dessert (100g serving)',
            align: 'left',
            value: 'name'
          },
          { text: 'Calories', value: 'calories' },
          { text: 'Fat (g)', value: 'fat' },
          { text: 'Carbs (g)', value: 'carbs' },
          { text: 'Protein (g)', value: 'protein' },
          { text: 'Iron (%)', value: 'iron' },
          { text: 'Alert'}
        ],
        desserts: [
          {
            name: '1',
            calories: 159,
            fat: 6.0,
            carbs: 24,
            protein: 4.0,
            iron: '1%',
          },
          {
            name: '2',
            calories: 237,
            fat: 9.0,
            carbs: 37,
            protein: 4.3,
            iron: '1%',
          },
          {
            name: '3',
            calories: 262,
            fat: 16.0,
            carbs: 23,
            protein: 6.0,
            iron: '7%'
          },
          {
            name: '4',
            calories: 305,
            fat: 3.7,
            carbs: 67,
            protein: 4.3,
            iron: '8%'
          },
          {
            name: '5',
            calories: 356,
            fat: 16.0,
            carbs: 49,
            protein: 3.9,
            iron: '16%'
          },
          {
            name: '6',
            calories: 375,
            fat: 0.0,
            carbs: 94,
            protein: 0.0,
            iron: '0%'
          },
          {
            name: '7',
            calories: 392,
            fat: 0.2,
            carbs: 98,
            protein: 0,
            iron: '2%'
          },
          {
            name: '8',
            calories: 408,
            fat: 3.2,
            carbs: 87,
            protein: 6.5,
            iron: '45%'
          },
          {
            name: '9',
            calories: 452,
            fat: 25.0,
            carbs: 51,
            protein: 4.9,
            iron: '22%'
          },
          {
            name: '10',
            calories: 518,
            fat: 26.0,
            carbs: 65,
            protein: 7,
            iron: '6%'
          }
        ],
        button:[],
      }
    }  
  }
</script>

<style>

</style>
