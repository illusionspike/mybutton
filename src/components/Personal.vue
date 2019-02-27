<template>
  <div>
    <v-toolbar flat color="white">
      <v-toolbar-title>Personal Information</v-toolbar-title>
      <v-divider
        class="mx-2"
        inset
        vertical
      ></v-divider>
      <v-spacer></v-spacer>
      <v-dialog v-model="dialog" max-width="500px">
        <v-btn slot="activator" color="primary" dark class="mb-2">New Item</v-btn>
        <v-card>
          <v-card-title>
            <span class="headline">{{ formTitle }}</span>
          </v-card-title>

          <v-card-text>
            <v-container grid-list-md>
              <v-layout wrap>
                <v-flex xs12 sm6 md4>
                  <v-text-field v-model="editedItem.name" label="Dessert name"></v-text-field>
                </v-flex>
                <v-flex xs12 sm6 md4>
                  <v-text-field v-model="editedItem.calories" label="Calories"></v-text-field>
                </v-flex>
                <v-flex xs12 sm6 md4>
                  <v-text-field v-model="editedItem.fat" label="Fat (g)"></v-text-field>
                </v-flex>
                <v-flex xs12 sm6 md4>
                  <v-text-field v-model="editedItem.carbs" label="Carbs (g)"></v-text-field>
                </v-flex>
                <v-flex xs12 sm6 md4>
                  <v-text-field v-model="editedItem.protein" label="Protein (g)"></v-text-field>
                </v-flex>
              </v-layout>
            </v-container>
          </v-card-text>

          <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn color="blue darken-1" flat @click="close">Cancel</v-btn>
            <v-btn color="blue darken-1" flat @click="save">Save</v-btn>
          </v-card-actions>
        </v-card>
      </v-dialog>
    </v-toolbar>
    <v-data-table
      :headers="headers"
      :items="desserts"
    :pagination.sync="pagination"
      class="elevation-1"
    >
      <template slot="items" slot-scope="props">
        <td class="text-xs-left">{{ props.item.no }}</td>
        <td class="text-xs-left">{{ props.item.name }}</td>
        <td class="text-xs-left">{{ props.item.tell }}</td>
        <td class="text-xs-left">{{ props.item.age }}</td>
        <td class="text-xs-left">{{ props.item.address }}</td>
        <td class="justify-left layout pl-20">
          <v-icon
            small
            class="mr-2"
            @click="editItem(props.item)"
          >
            edit
          </v-icon>
          <v-icon
            small
            @click="deleteItem(props.item)"
          >
            delete
          </v-icon>
        </td>
      </template>
      <template slot="no-data">
        <v-btn color="primary" @click="initialize">Reset</v-btn>
      </template>
    </v-data-table>
  </div>
</template>

<script>
export default {
  data: () => ({
    pagination: {
        rowsPerPage: -1
    },
    dialog: false,
    headers: [
      {
        text: "ID",
        align: "left",
        value: "no"
      },
      { text: "Name-Surname", value: "name" },
      { text: "Tell", value: "age" },
      { text: "Address", value: "tell" },
      { text: "Age", value: "address" },
      { text: "Actions", value: "name", sortable: false }
    ],
    desserts: [],
    editedIndex: -1,
    editedItem: {
      name: "",
      calories: 0,
      fat: 0,
      carbs: 0,
      protein: 0
    },
    defaultItem: {
      name: "",
      calories: 0,
      fat: 0,
      carbs: 0,
      protein: 0
    }
  }),
  computed: {
    formTitle() {
      return this.editedIndex === -1 ? "New Item" : "Edit Item";
    }
  },
  watch: {
    dialog(val) {
      val || this.close();
    }
  },
  created() {
    this.initialize();
  },
  methods: {
    initialize() {
      this.desserts = [
        {
          no: "1",
          name: "ศุภกิตต์ ธรรมชาติสุนทรี",
          age: "22 ปี",
          tell: "086-507-6630",
          address: "34/81 ม.วังทอง ถนนวิภาวดีรังสิต แขวงสนามบิน เขตดอนเมือง กทม. 10210"
  
        },
        {
          no: "2",
          name: "มิ้นท์ ณัฐวรา",
          age: "25 ปี",
          tell: "081-234-5678",
          address: "2038 ถนนลาดพร้าว แขวงวังทองหลาง เขตวังทองหลาง กรุงเทพ 10310"
        },
        {
          no: "3",
          name: "ฐิสา วริฏฐิสา",
          age: "26 ปี",
          tell: "081-234-7788",
          address: "46/148 ม.3 ถ.ศรีสมาน ต.บ้านใหม่ อ.ปากเกร็ด จ.นนทบุรี 11120"
        },
        {
          no: "4",
          name: "ณปภัช วัฒนากมลวุฒิ",
          age: "30 ปี",
          tell: "081-456-7788",
          address: "28/38 ถนนยิงเป้า ต.สนามจันทร์ อ.เมือง จ.นครปฐม 73000"
        },
        {
          no: "5",
          name: "เฌอมาลย์ บุญยศักดิ์",
          age: "33 ปี",
          tell: "081-456-5050",
          address: "72/33 ถ.ศุขประยูร ต.หน้าเมือง อ.เมือง จ.ฉะเชิงเทรา 24000"
        },
        {
          no: "6",
          name: "แพท ณปภา",
          age: "35 ปี",
          tell: "081-456-7000",
          address: "104/32 หมู่ 2 ถนนพระยาสัจจา ต.เสม็ด อ.เมือง จ.ชลบุรี 20000"
        },
        {
          no: "7",
          name: "ชญานิษฐ์ จามิกรณ์",
          age: "36 ปี",
          tell: "081-456-7008",
          address: "109/10 ถ.จันทอุดม ต.เชิงเนิน อ.เมือง จ.ระยอง 21000"
        },
        {
          no: "8",
          name: "วีรวัลย์ โพธิ์งาม",
          age: "25 ปี",
          tell: "081-456-7008",
          address: "459/98 ถ.เจริญเมือง ต.วัดเกตุ อ.เมือง จ.เชียงใหม่ 50000"
        },
        {
          no: "9",
          name: "พิ้งค์กี้ สาวิกา",
          age: "30 ปี",
          tell: "081-456-7888",
          address: "919/118 ม.10 ถ.พหลโยธิน ต.นครสวรรค์ตก อ.เมือง จ.นครสวรรค์ 60000"
        },
        {
          no: "10",
          name: "เฟี้ยว์ฟ้าว สุดสวิงริงโก้",
          age: "36 ปี",
          tell: "081-786-7888",
          address: "362/10 ม.3 ถ.พิษณุโลก-หล่มสัก ต.อรัญญิก อ.เมือง จ.พิษณุโลก 65000"
        }
      ];
    },
    editItem(item) {
      this.editedIndex = this.desserts.indexOf(item);
      this.editedItem = Object.assign({}, item);
      this.dialog = true;
    },
    deleteItem(item) {
      const index = this.desserts.indexOf(item);
      confirm("Are you sure you want to delete this item?") &&
        this.desserts.splice(index, 1);
    },
    close() {
      this.dialog = false;
      setTimeout(() => {
        this.editedItem = Object.assign({}, this.defaultItem);
        this.editedIndex = -1;
      }, 300);
    },
    save() {
      if (this.editedIndex > -1) {
        Object.assign(this.desserts[this.editedIndex], this.editedItem);
      } else {
        this.desserts.push(this.editedItem);
      }
      this.close();
    }
  }
};
</script>