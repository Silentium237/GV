<template>
<div align="center" justify="space-between">
  <PeopleEdit
    v-if="dialog"
    :item="itemPeople"/>
  <div class="fancy-title pt-6 pb-6">
    People
  </div>
  <v-card
  width="85%">
    <v-card-title>
      <v-text-field
        v-model="search"
        append-icon="mdi-magnify"
        label="Search"
        single-line
        hide-details
      ></v-text-field>
    </v-card-title>

    <v-data-table
      :headers="headers"
      :items="desserts"
      :search="search"
      @click:row="alert"
    >
      <template v-slot:item.image="{ item }">
        <v-list-item>
          <v-list-item-avatar>
            <v-img :src="item.image" :alt="item.name"  ></v-img>
          </v-list-item-avatar>
        </v-list-item>
      </template>
      <template v-slot:item.addPhone="{ item }">
        <v-list-item>
          <v-list-item-avatar>
            <v-img src="https://img2.freepng.ru/20180319/agw/kisspng-iphone-computer-icons-telephone-symbol-clip-art-telephone-icon-blue-gradient-5ab065f7cab439.0138874915215098798303.jpg" max-width="35%" height="35%" :alt="item.name"  ></v-img>
          </v-list-item-avatar>
          <div>{{item.addPhone}}</div>
        </v-list-item>
      </template>
      <template v-slot:item.mobilePhone="{ item }">
        <v-list-item>
          <v-list-item-avatar>
            <v-img src="https://img2.freepng.ru/20180319/agw/kisspng-iphone-computer-icons-telephone-symbol-clip-art-telephone-icon-blue-gradient-5ab065f7cab439.0138874915215098798303.jpg" max-width="35%" height="35%" :alt="item.name"></v-img>
          </v-list-item-avatar>
          <div>{{item.mobilePhone}}</div>
        </v-list-item>
      </template>
    </v-data-table>
  </v-card>
</div>
</template>

<script>
import PeopleEdit from "../components/PeopleEdit";
export default {
  name: "people",
  components: {PeopleEdit},
  data () {
    return {
      itemPeople: [],
      dialog: false,
      search: '',
      headers: [
        { text: 'Avatar', value: 'image' },
        {
          text: 'Name',
          align: 'start',
          filterable: false,
          value: 'name',
        },
        { text: 'Position', value: 'position' },
        { text: 'Email', value: 'email' },
        { text: 'Add Phone', value: 'addPhone' },
        { text: 'Mobile Phone', value: 'mobilePhone' },
      ],
      desserts: [
        {
          image:  require("../assets/images/img.png"),
          name: 'Ivan Dorn',
          position: 'engineers',
          email: 'ivan@gmail.com',
          addPhone: 125,
          mobilePhone: '+37544-688-88-99',
        },
        {
          image: 'https://picsum.photos/250/300?image=783',
          name: 'Pavel Ivanov',
          position: 'engineers',
          email: 'pavel_ivanov@gmail.com',
          addPhone: 124,
          mobilePhone: '+37544-688-88-99',
          workStart: '24.12.2020'
        },
        {
          image: 'https://picsum.photos/250/300?image=1006',
          name: 'Egor Petrov',
          position: 'builder',
          email: 'egor_petrov@gmail.com',
          addPhone: 124,
          mobilePhone: '+37544-688-88-99',
        },
        {
          image: 'https://picsum.photos/250/300?image=146',
          name: 'Jon Smith',
          position: 'accountant',
          email: 'e_p@gmail.com',
          addPhone: 124,
          mobilePhone: '+37544-688-88-99',
        },
        {
          image: 'https://picsum.photos/250/300?image=839',
          name: 'Evgeni Kyky',
          position: 'accountant',
          email: 'evgeni_kyky@gmail.com',
          addPhone: 124,
          mobilePhone: '+37544-688-88-99',
        },
        {
          image: 'https://picsum.photos/250/300?image=145',
          name: 'Jelly Dron',
          position: 'accountant',
          email: 'jelly_dron@gmail.com',
          addPhone: 124,
          mobilePhone: '+37544-688-88-99',
        },
        {
          image: 'https://picsum.photos/250/300?image=145',
          name: 'Lolli Pop',
          position: 'engineer',
          email: 'lolli_pop@gmail.com',
          addPhone: 124,
          mobilePhone: '+37544-688-88-99',
        },
        {
          image: 'https://picsum.photos/250/300?image=145',
          name: 'Honey Bear',
          position: 'engineer',
          email: 'honey_bear@gmail.com',
          addPhone: 124,
          mobilePhone: '+37544-688-88-99',
        },
        {
          image: 'https://picsum.photos/250/300?image=1006',
          name: 'Kit Kat',
          position: 'artist',
          email: 'kit_kat@gmail.com',
          addPhone: 124,
          mobilePhone: '+37544-688-88-99',
        },
        {
          image: 'https://picsum.photos/250/300?image=1006',
          name: 'Supper Man',
          position: 'artist',
          email: 'supper_man@gmail.com',
          addPhone: 124,
          mobilePhone: '+37544-688-88-99',
        },
      ],
    }
  },
  methods:{
    alert(item){
      this.itemPeople = item
      // alert(item.name)
      this.dialog = true
    }
  }
}
</script>

<style scoped>

</style>
