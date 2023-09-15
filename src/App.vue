<script setup>
  import{ ref } from "vue";
  
  const travel = ref("");
  const money = ref(0);

  const Details = ref({
    name: "",
    tel: "",
    date: "",
    time: "",
    tables: ""
  });
  
  
  const travelList = ref([
    {name:'Playworks.cafeart', price:80, size: {s:80, m: 150, l: 200}, img:"https://i.pinimg.com/564x/52/be/fc/52befc75732e06edb69c844651ee84b1.jpg" },
    {name:'Malee bakery ', price: 50 , size: {s:80, m: 150, l: 200}, img:"https://i.pinimg.com/564x/af/db/72/afdb7292e2982a91883b5f40df53ab31.jpg" },
    {name:'Kramfeine', price: 90 , size: {s:90, m: 120, l: 150}, img:"https://i.pinimg.com/564x/6c/7d/b5/6c7db54d152fa259bad7ba4a0af3bcc5.jpg" },
  ]);
  
  const bookingList = ref([
  ]);

  

  function booking(restaurant, details) {

  const bookingData = {
    restaurantName: restaurant.name,
    name: details.name,
    tel: details.tel,
    date: details.date,
    time: details.time,
    tables: details.tables,
  };
  
  bookingList.value.push(bookingData);

  Details.name = '';
  Details.tel = '';
  Details.date = '';
  Details.time = '';
  Details.tables = '';
  alert("Booking Complete!!! , Please Check Your Booking Details at The bottom of page")
}

  
  
//   //function
// function booking(name){
//   //name -> bookingList []
//   bookingList.value.push(name)
// }

</script>

<template>
  <img src="https://i.pinimg.com/564x/95/15/13/9515134ad6a7645150c3f5560186822f.jpg" width="350" class="img-fluid"  alt="...">
  <img src="https://i.pinimg.com/564x/f2/20/00/f220008ff867913d96bb1b9f1951d873.jpg" width="250" class="img-fluid"  alt="...">
  <div>
  </div>
  <div class="container text-center" style="background-color: ; border-radius: 20px;">
    <div class="row" align="center">
      <div class="col" v-for="(item, index) in travelList" :key="index">
        <div class="card" style="width: 18rem; background-color: #e0d9e0; margin: 25px; border-radius: 30px;">
          <img :src="item.img" class="card-img-top" alt="...">
          <div class="card-body">
            <h5 class="card-title">{{ item.name }}</h5>
            <p class="card-text">Enjoyyyyyy.</p>
             <br>
            <a href="#" class="btn" @click="booking(item, Details)">⤑ จองโต๊ะ</a>
          </div>
        </div>
      </div>
    </div>
  </div> <br>
  

  <h2 style="color: rgb(3, 1, 1) ; font-family: 'Mali', cursive; ">รายละเอียดการจอง ♡</h2>
   <br>
  <div class="container-input" style="background-color: #fff;">
    <br>
    <h4 style="color: rgb(245, 0, 0); font-weight: bold;"></h4>
    <div class="cont">
          <div class="text-input">
            Name ✦ &nbsp; <input type="text" v-model="Details.name" required> 
          </div><p></p>
          <div class="text-input">
            Tel ✦  &nbsp; <input type="tel" v-model="Details.tel" required> 
          </div><p></p>
          <div class="text-input">  
            D/M/Y ✦ &nbsp; <input type="date" v-model="Details.date" required>
          </div><p></p>
          <div class="text-input">
            Time ✦ &nbsp; <input type="time" v-model="Details.time" required>
          </div><p></p>
          <div class="text-input">
            Tables ✦ &nbsp; <input type="number" v-model="Details.tables" required> 
          </div>
    </div>
  </div>
  <table class="table table-dark table-striped" v-if="bookingList.length > 0">
  <thead>
    <h4>Details</h4>
    <tr>
      <th scope="col">Coffe 。</th>
      <th scope="col">Name 。</th>
      <th scope="col">Tel 。</th>
      <th scope="col">DD/MM/YYY 。</th>
      <th scope="col">Time 。 </th>
      <th scope="col">Tables 。</th>
    </tr>
  </thead>
  <tbody>
    <tr v-for="(booking, index) in bookingList" :key="index">
      <td>{{ booking.restaurantName }}</td>
      <td>{{ booking.name }}</td>
      <td>{{ booking.tel }}</td>
      <td>{{ booking.date }}</td>
      <td>{{ booking.time }}</td>
      <td>{{ booking.tables }}</td>
    </tr>
  </tbody>
</table> <br>

  
</template>
