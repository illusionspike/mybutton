<template>
<v-data-table
    :headers="headers"
    :items="desserts"
    :pagination.sync="pagination"
    class="elevation-1"
  >
    <template slot="items" slot-scope="props">
      <td class="text-xs-left">{{ props.item.no }}</td>
      <td class="text-xs-left">{{ props.item.name }}</td>
      <td class="text-xs-left">{{ props.item.age }}</td>
      <td class="text-xs-left">{{ props.item.tell }}</td>
      <td class="text-xs-left">{{ props.item.address }}</td>
      <td class="text-xs-left">
        <v-btn v-if="props.item.state == 1" color="red" @click="openMap(props.item.no-1)"></v-btn>
        <v-btn v-if="props.item.state == 0" color="green"></v-btn>
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
            text: 'ID',
            align: 'left',
            value: 'no'
          },
          { text: 'Name-Surname', value: 'name' },
          { text: 'Age', value: 'age' },
          { text: 'Tell', value: 'tell' },
          { text: 'Address', value: 'address' },
          { text: 'Alert', value: 'state'}
        ],
        desserts: [
        {
          no: "1",
          name: "ศุภกิตต์ ธรรมชาติสุนทรี",
          age: "22 ปี",
          tell: "086-507-6630",
          address: "34/81 ม.วังทอง ถนนวิภาวดีรังสิต แขวงสนามบิน เขตดอนเมือง กทม. 10210",
          state: 0
  
        },
        {
          no: "2",
          name: "มิ้นท์ ณัฐวรา",
          age: "25 ปี",
          tell: "081-234-5678",
          address: "2038 ถนนลาดพร้าว แขวงวังทองหลาง เขตวังทองหลาง กรุงเทพ 10310",
          state: 0
        },
        {
          no: "3",
          name: "ฐิสา วริฏฐิสา",
          age: "26 ปี",
          tell: "081-234-7788",
          address: "46/148 ม.3 ถ.ศรีสมาน ต.บ้านใหม่ อ.ปากเกร็ด จ.นนทบุรี 11120",
          state: 0
        },
        {
          no: "4",
          name: "ณปภัช วัฒนากมลวุฒิ",
          age: "30 ปี",
          tell: "081-456-7788",
          address: "28/38 ถนนยิงเป้า ต.สนามจันทร์ อ.เมือง จ.นครปฐม 73000",
          state: 0
        },
        {
          no: "5",
          name: "เฌอมาลย์ บุญยศักดิ์",
          age: "33 ปี",
          tell: "081-456-5050",
          address: "72/33 ถ.ศุขประยูร ต.หน้าเมือง อ.เมือง จ.ฉะเชิงเทรา 24000",
          state: 0
        },
        {
          no: "6",
          name: "แพท ณปภา",
          age: "35 ปี",
          tell: "081-456-7000",
          address: "104/32 หมู่ 2 ถนนพระยาสัจจา ต.เสม็ด อ.เมือง จ.ชลบุรี 20000",
          state: 0
        },
        {
          no: "7",
          name: "ชญานิษฐ์ จามิกรณ์",
          age: "36 ปี",
          tell: "081-456-7008",
          address: "109/10 ถ.จันทอุดม ต.เชิงเนิน อ.เมือง จ.ระยอง 21000",
          state: 0
        },
        {
          no: "8",
          name: "วีรวัลย์ โพธิ์งาม",
          age: "25 ปี",
          tell: "081-456-7008",
          address: "459/98 ถ.เจริญเมือง ต.วัดเกตุ อ.เมือง จ.เชียงใหม่ 50000",
          state: 0
        },
        {
          no: "9",
          name: "พิ้งค์กี้ สาวิกา",
          age: "30 ปี",
          tell: "081-456-7888",
          address: "919/118 ม.10 ถ.พหลโยธิน ต.นครสวรรค์ตก อ.เมือง จ.นครสวรรค์ 60000",
          state: 0
        },
        {
          no: "10",
          name: "เฟี้ยว์ฟ้าว สุดสวิงริงโก้",
          age: "36 ปี",
          tell: "081-786-7888",
          address: "362/10 ม.3 ถ.พิษณุโลก-หล่มสัก ต.อรัญญิก อ.เมือง จ.พิษณุโลก 65000",
          state: 0
        }
        ],
        button:[],
      }
    },
    mounted(){
      this.handle = setInterval(() => {
        axios.get('http://35.198.196.233:4000/read/AllstatusButton')
        .then((response)=>{
            this.button = response.data;
            console.log(this.button[0].data)
            if(this.button[0].data == 1){
              this.desserts[0].state = 1
            }else{
              this.desserts[0].state = 0
            }
        })
      },3000)
    },
    methods:{
        openMap: function(temp){
          console.log(temp)
          var buttonID = this.button[temp].ID
          var buttonData = 0
          var chageAPI = 'http://35.198.196.233:4000/updatestatus/AllstatusButton/'+buttonID+'/'+buttonData
          console.log(chageAPI)
          axios.get(chageAPI)
          .then((response)=>{
            console.log(response.data)
          })
          this.desserts[temp].state = 0
          var source = 'โรงพยาบาลศิริราช';
          var destination = 'มหาวิทยาลัยมหิดล';
          var link = 'https://www.google.com/maps/dir/?api=1&origin='+source+'&destination='+destination+'&travelmode=driving';
          window.open(link);
        }
    }
  }
</script>