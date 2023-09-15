<script setup>
import { ref } from 'vue';

const travel = ref("");
const money = ref(0);

// เก็บข้อมูลการจองร้าน
const bookinglist = ref([]);

// ข้อมูลการจองโต๊ะ
const bookingData = ref({
  name: "",
  phoneNumber: "",
  date: "",
  count_tables: ""
});

// function สำหรับการจอง
function booking(restaurantName, data) {
  bookinglist.value.push({
    order: bookinglist.value.length + 1, // การจองลำดับที่
    name: data.name,
    restaurant: restaurantName,
    phoneNumber: data.phoneNumber,
    date: data.date,
    count_tables: data.count_tables
  });
  // ล้างข้อมูลหลังจากจอง
  bookingData.value = {
    name: "",
    phoneNumber: "",
    date: "",
    count_tables: ""
  };
}

const travellist = ref ([
  {name:'ท่าช้าง', 
  price:80, 
  size:{s: 80,m: 150, l: 200}, 
  img:"https://p-u.popcdn.net/event_details/posters/000/008/856/original/cfe1b94d03c5137faf1500f98117421e9f2ac9db.jpg?1590662796"},

  {name:'GoodView', 
  price:120, 
  size:{s: 120,m: 180, l: 250}, 
  img:"https://th.bing.com/th/id/OIP.R9A5Gpn-DpOChTHyuic_sAHaFj?pid=ImgDet&rs=1"},

  {name:'RiverSide' , 
  price:150, 
  size:{s: 150,m: 190, l: 300}, 
  img:"https://th.bing.com/th/id/R.ab9802205edc889cdc62f84af245316c?rik=EUFmNFFfO91eJA&riu=http%3a%2f%2fwww.dooasia.com%2fwp-content%2fuploads%2f2018%2f05%2fThe-RiverSide-%e0%b9%80%e0%b8%8a%e0%b8%b5%e0%b8%a2%e0%b8%87%e0%b9%83%e0%b8%ab%e0%b8%a1%e0%b9%88-7-696x464.jpg&ehk=IfTrEAF8BEuE9hJhtMKHQNYZmV%2boSJEesY%2fzQmFNYoo%3d&risl=&pid=ImgRaw&r=0"},

  {name:'WarmUp', 
  price:100, 
  size:{s: 100,m: 200, l: 500}, 
  img:"https://d136usn7jnoe61.cloudfront.net/pictures/21526/s2n_0002_p1d06tc4oou8jlkvr0l1mag1grj6.jpg"},

  {name:'ตะวันแดง', 
  price:90, 
  size:{s: 90,m: 250, l: 700}, 
  img:"https://th.bing.com/th/id/R.6fd3de7109e6a325c0d72efb53de2050?rik=Aa1zQxZXAWtxSg&riu=http%3a%2f%2ftawandang.com%2fwp-content%2fuploads%2f2017%2f08%2fTWDjang-Chaeng-Wattana.jpg&ehk=WHcn32JlAx8ZTvDdAHwMb81EWoU%2fiVLDtNNd6K%2bP6Ao%3d&risl=&pid=ImgRaw&r=0"},

  {name: 'OverNight',
  price:90,
  img:"https://scontent.fbkk29-9.fna.fbcdn.net/v/t39.30808-6/358585862_234241546168163_6229403025791880541_n.jpg?_nc_cat=104&ccb=1-7&_nc_sid=49d041&_nc_eui2=AeFAdBePSCKzxhk2V77JHqgXo5L0fUorXoWjkvR9SitehRSk4yY8Ye43VUnlm_gQLyquQYuwCAc_qhn3NCz76_xA&_nc_ohc=EO3UeZJfWygAX_z_jT2&_nc_ht=scontent.fbkk29-9.fna&oh=00_AfBmnUPe_ECskO763HPlBw-aAhmTjVAoVDZptizHfafSEg&oe=6508168B"}
]);
</script>


<template>
  <div class="header">
    <h1>🍾🍹LH Booking🍹🍾</h1>
  </div>
   <div class="p-3 m-0 border-0 bd-example m-0 border-0">
   <div class="text-center">
     <div class="row row-cols-1 row-cols-md-3 g-4">
       <div class="col" v-for="(i,name) in travellist" :key="index">
         <div class="card text-bg-dark h-100" style="width:18rem">
         <img v-if="i.img" :src="i.img" class="card-img-top" alt="..." />
         <div class="card-body">
         <h5 class="card-title">{{ i.name }}</h5>
          
          <a class="btn btn-primary" @click="booking(i.name, bookingData)">จองโต๊ะ</a>
         </div>
         </div>
       </div>
     </div>
   </div>
 </div>
  <div class="flex-container">
    <form class="row g-3" style="gap: 20px;">
      <div class="col-md-3">
        <label for="validationDefaulto1" class="form.label" style="color: #ffff">
          ชื่อคนจอง:<input type="text" v-model="bookingData.name" class="form-control" id="validationDefault01" required></label>
      </div>
      <div class="col-md-3">
        <label for="validationDefault02" class="form-label" style="color: #ffff">
          เบอร์โทร:<input type="text" v-model="bookingData.phoneNumber" class="form-control" id="validationDefault02" required></label>
      </div>
      <div class="col-md-3">
        <label for="validationDefault03" class="form-label" style="color: #ffff">
          วันที่:<input type="date" v-model="bookingData.date" class="form-control" id="validationDefault03" required></label>
      </div>
      <div class="col-md-2">
        <label for="validationDefault04" class="form-label" style="color: #ffff">
          จำนวนโต๊ะ:<input type="text" v-model="bookingData.count_tables" class="form-control" id="validationDefault04" required></label>
      </div>
    </form>
  </div>
            <br>
  <table class="table table-dark table-striped" v-if="bookinglist.length > 0">
    <thead>
      <tr>
        <th scope="col">#</th>
        <th scope="col">ชื่อคนจอง</th>
        <th scope="col">ร้านที่จอง</th>
        <th scope="col">เบอร์โทรศัพท์</th>
        <th scope="col">วันที่</th>
        <th scope="col">จำนวนโต๊ะ</th> <!-- เปลี่ยนนี่เป็น "จำนวนโต๊ะ" แทน -->
      </tr>
    </thead>
    <tbody>
      <tr v-for="(item, index) in bookinglist" :key="index">
        <th>{{ item.order }}</th>
        <td>{{ item.name }}</td>
        <td>{{ item.restaurant }}</td>
        <td>{{ item.phoneNumber }}</td>
        <td>{{ item.date }}</td>
        <td>{{ item.count_tables }}</td> <!-- เปลี่ยนนี่เป็น "item.count_tables" แทน -->
      </tr>
    </tbody>
  </table>

</template>

<style>

body{
  background: linear-gradient(to bottom,#6d6875,#ffcdb2,#6d6875);

}
.flex-container {
    display: flex; /* กำหนดให้เป็นกล่อง flex */
    justify-content: center; /* จัดการความระหว่างองค์ประกอบตามแนวนอน */
    align-items: center; /* จัดการความสูงแนวตั้ง */
    border: 2px solid #ffff;
    padding: 10px; /* เพิ่มขอบรอบกล่อง */
}
.header {
    
    color: #f2f2f2; /* สีข้อความ */
    padding: 20px; /* ระยะห่างรอบขอบ */
    text-align: center; /* จัดข้อความให้อยู่กึ่งกลาง */
}
.header h1 {
    font-size: 36px; /* ขนาดข้อความ */
    margin: 0; /* ลบระยะห่างด้านบนและด้านล่าง */
}
</style>