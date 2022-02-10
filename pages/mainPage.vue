<template>
  <v-container class="lighten-5">
    <v-row no-gutters>

      <v-col cols="4">
        <v-row no-gutters>
          <v-col cols="12">
            <v-card class="ma-2">
              <BarChart :data="barChartData" :options="barChartOptions" :height="400"/>
            </v-card>
          </v-col>
          <v-col cols="12">
            <v-card class="ma-2">
              <Users/>
            </v-card>
          </v-col>
        </v-row>
      </v-col>

      <v-col cols="2">
        <v-row no-gutters>
          <v-col cols="12">
            <v-card class="ma-2">
              <Progress/>
            </v-card>
          </v-col>
          <v-col cols="12">
            <v-card class="ma-2">
              <Birthday/>
            </v-card>
          </v-col>
        </v-row>

      </v-col>
      <v-col cols="3">
        <v-card
          class="ma-2"
        >
          <TasksMainPage/>
        </v-card>
      </v-col>
      <v-col cols="3">
        <v-card
          class="ma-2"
        >
          <LineChart :data="barChartData" :options="barChartOptions" :width="100" :height="200"/>
        </v-card>
      </v-col>
    </v-row>
  </v-container>


</template>

<script>
import BarChart from "../components/BarChart";
import Progress from "../components/Progress";
import Birthday from "../components/Birthday";
import TasksMainPage from "../components/TasksMainPage";
import Users from "../components/Users";

export default {
  name: "mainPage",
  components: {Users, TasksMainPage, Birthday, Progress, BarChart},
  data() {
    return {
      barChartData: {
        labels: [
          'Critical',
          'Major',
          'Moderate',
          'Minor',
          'Cosmetic',
        ],
        datasets: [
          {
            labels: ['Red', 'Orange', 'Yellow', 'Green', 'Blue'],
            data: [15, 25, 10, 20, 30],
            backgroundColor: ['red', 'orange', 'yellow', 'green', 'blue'],
            width: 5,
          },
          // {
          //   label: 'Pages Views',
          //   data: [30, 24, 57, 23, 68, 72, 25, 64, 133, 143, 165, 33, 56],
          //   backgroundColor: '#2f4b7c'
          // },
          // {
          //   label: 'Users',
          //   data: [45, 65, 30, 53, 34, 35, 26, 37, 34, 45, 67, 87, 98],
          //   backgroundColor: '#665191'
          // }
        ]
      },
      barChartOptions: {
        responsive: true,
        legend: {
          display: true
        },
        title: {
          display: true,
          text: 'Information',
          fontSize: 18,
          fontColor: 'black'
        },
        // tooltips: {
        //   backgroundColor: '#17BF62'
        // },
        // scales: {
        //   xAxes: [
        //     {
        //       gridLines: {
        //         display: false
        //       }
        //     }
        //   ],
        //   yAxes: [
        //     {
        //       ticks: {
        //         beginAtZero: true
        //       },
        //       gridLines: {
        //         display: false
        //       }
        //     }
        //   ]
        // }
      }
    }
  }
}
</script>

<!--<style scoped>-->

<!--</style>-->
<!--<template>-->
<!--  <client-only>-->
<!--    <my-line :data="data"></my-line>-->
<!--  </client-only>-->
<!--</template>-->


<!--<script>-->
<!--export default {-->
<!--  name: "mainPage",-->
<!--  data() {-->
<!--    return {-->
<!--      barChartData: {-->
<!--        labels: [-->
<!--          '2019-06',-->
<!--          '2019-07',-->
<!--          '2019-08',-->
<!--          '2019-09',-->
<!--          '2019-10',-->
<!--          '2019-11',-->
<!--          '2019-12',-->
<!--          '2020-01',-->
<!--          '2020-02',-->
<!--          '2020-03',-->
<!--          '2020-04',-->
<!--          '2020-05'-->
<!--        ],-->
<!--        datasets: [-->
<!--          {-->
<!--            label: 'Visits',-->
<!--            data: [10, 15, 20, 30, 40, 50, 60, 70, 34, 45, 11, 78, 45],-->
<!--            backgroundColor: '#003f5c'-->
<!--          },-->
<!--          {-->
<!--            label: 'Pages Views',-->
<!--            data: [30, 24, 57, 23, 68, 72, 25, 64, 133, 143, 165, 33, 56],-->
<!--            backgroundColor: '#2f4b7c'-->
<!--          },-->
<!--          {-->
<!--            label: 'Users',-->
<!--            data: [45, 65, 30, 53, 34, 35, 26, 37, 34, 45, 67, 87, 98],-->
<!--            backgroundColor: '#665191'-->
<!--          }-->
<!--        ]-->
<!--      },-->
<!--      barChartOptions: {-->
<!--        responsive: true,-->
<!--        legend: {-->
<!--          display: false-->
<!--        },-->
<!--        title: {-->
<!--          display: true,-->
<!--          text: 'Google analytics data',-->
<!--          fontSize: 24,-->
<!--          fontColor: '#6b7280'-->
<!--        },-->
<!--        tooltips: {-->
<!--          backgroundColor: '#17BF62'-->
<!--        },-->
<!--        scales: {-->
<!--          xAxes: [-->
<!--            {-->
<!--              gridLines: {-->
<!--                display: false-->
<!--              }-->
<!--            }-->
<!--          ],-->
<!--          yAxes: [-->
<!--            {-->
<!--              ticks: {-->
<!--                beginAtZero: true-->
<!--              },-->
<!--              gridLines: {-->
<!--                display: false-->
<!--              }-->
<!--            }-->
<!--          ]-->
<!--        }-->
<!--      }-->
<!--    }-->
<!--  }-->
<!--}-->
<!--</script>-->
<!--<template>-->
<!--  <div>-->
<!--    <my-line v-if="showLine" :data="lineData" :options="options">-->
<!--  </div>-->
<!--</template>-->

<!--<script>-->
<!--export default {-->
<!--  data () {-->
<!--    return {-->
<!--      showLine: false-->
<!--    }-->
<!--  },-->
<!--  mounted () {-->
<!--    this.showLine = true // showLine will only be set to true on the client. This keeps the DOM-tree in sync.-->
<!--  },-->
<!--  asyncData () {-->
<!--    const lineData = {} // some data-->
<!--    const options = {} // some options-->
<!--    return { lineData, options }-->
<!--  }-->
<!--}-->
<!--</script>-->
