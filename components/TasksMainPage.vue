<template>
  <v-card
    class="mx-auto"
    max-width="500"
  >
    <div style="font-size: 18px; color: black; font-weight: bold" class="pa-2" align="center" justify="space-between" >
      Tasks
    </div>
    <v-list shaped
            style="max-height: 500px"
            class="overflow-y-auto">>
      <v-list-item-group
        v-model="model"
        multiple
      >
        <template v-for="(item, i) in items">
          <v-divider
            v-if="!item"
            :key="`divider-${i}`"
          ></v-divider>

          <v-list-item
            v-else
            :key="`item-${i}`"
            :value="item"
            active-class="deep-purple--text text--accent-4"
          >
            <template v-slot:default="{ active }">
              <v-list-item-content>
                <v-list-item-title v-text="item"></v-list-item-title>
              </v-list-item-content>

              <v-list-item-action>
                <v-checkbox
                  :input-value="active"
                  color="deep-purple accent-4"
                ></v-checkbox>
              </v-list-item-action>
            </template>
          </v-list-item>
        </template>
      </v-list-item-group>
    </v-list>
  </v-card>
</template>

<script>
export default {
  name: "TasksMainPage",
  data: () => ({
    items: [
      'Create new page in this application',
      'Add back end part in this product ',
      'Do not forget about server side rendering ',
      'Edit style in this project ',
      'Add registration page',
      'Add back end part in this product ',
      'Do not forget about server side rendering ',
      'Edit style in this project ',
      'Add registration page',
      'Edit style in this project ',
      'Add registration page',
    ],
    model: ['Carrots'],
  }),
}
</script>

<style scoped>

</style>
