<template>
        <!-- <div>
        Lat <input type="text" v-model="lati">  
        Long <input type="text" v-model="lati"> 

        <button @click="fetchPosts()" class="btn btn-primary">show more</button> 
        {{ lat }}{{ lon }} -->

    <!-- </div> -->
<div class="container">
    <div class="row">
     <h1 class="subject">  Weather for 5 days ,every 3 hours</h1>
      <!-- <div class="col">Latitude :{{ lati }}</div>
      <div class="col">Longitude :{{ long }}</div> -->
      <div class="input-group">
  <span class="input-group-text border-purple">Latitude AND Longitude</span>
  <input type="text" aria-label="Latitude" class="form-control text " v-model="lati">
  <input type="text" aria-label="Longitude" class="form-control text" v-model="long">
  <button @click="fetchPosts()" class="btn form "><img src="https://cdn-icons-png.flaticon.com/128/12271/12271129.png" class="iconbutton"></button> 
  </div>
    </div>
    <div class="row ">
        <div class="col-4 " >
            <div class="col-10  " v-for="(i,index) in items.list" :key="index">
    <div id="list-example">
      <a  class="card borderpurple " :href="`#`+index"><img :src="`https://openweathermap.org/img/wn/`+ i.weather[0].icon +`@2x.png`" class="card-img" style="max-width: 60px; ">{{items.list[index].dt_txt}}</a>
      
        </div>
    </div>
    </div>
        <div class="col-8 ">
            <div class="card h-80 container borderblue" v-for="(i,index) in items.list" :key="index">
            <div data-bs-spy="scroll" data-bs-target="#list-example" data-bs-smooth-scroll="true" class="scrollspy-example" tabindex="0" :id="index">
                <div class="row">
                  <div class="col-md-4">
                    <b class="date">DATE</b><br><p class="text">{{items.list[index].dt_txt}}</p> 
                    <img :src="`https://openweathermap.org/img/wn/`+ i.weather[0].icon +`@2x.png`" class="card-img" alt="..." style="max-width: 140px; ">
                     
                  </div>
                  <div class="col">
                    <h4 class="text"><strong>{{ items.city.name}} , {{ items.city.country }}</strong></h4>
                    <h5 class="text"> Feels like {{i.main.temp}}° C</h5>
                <div class="row justify-content-end text">
                  <div class="col-sm-6 col-md-6"><p><img  class="icontemp" src="https://cdn-icons-png.flaticon.com/128/5826/5826412.png" alt="temp_mim">   {{ i.main.temp_min }} ° C</p></div>
                  <div class="col-sm-6 col-md-6"><p><img  class="icontemp" src="https://cdn-icons-png.flaticon.com/128/5826/5826433.png" alt="temp_max">  {{ i.main.temp_max }} ° C</p></div>
                  <div class="col-sm-6 col-md-6"><p><img class="icontemp" src="https://cdn-icons-png.flaticon.com/128/4839/4839415.png" alt="description"> : {{i.weather[0].description}}</p></div>
                  <div class="col-sm-6 col-md-6"><p><img class="icontemp" src="https://cdn-icons-png.flaticon.com/128/10660/10660822.png" alt="humidity"> : {{ i.main.humidity }} %</p></div>
                  <div class="col-sm-6 col-md-6"><p><img class="iconhpa" src="https://cdn-icons-png.flaticon.com/512/425/425798.png" alt="visibility"> : {{ i.visibility /1000}} km</p></div>
                  <div class="col-sm-6 col-md-6"><p><img class="iconhpa" src="https://cdn-icons-png.flaticon.com/128/556/556958.png" alt="pressure"> : {{ i.main.pressure}} hPa </p></div>
                  <div class="col-sm-6 col-md-6"><p>Cloud : {{i.clouds.all}} % </p></div>
                  <div class="col-sm-6 col-md-6"><p>Wind Speed: {{ i.wind.speed }} Km/hr</p></div>
                </div>
                  </div>
                </div>

        </div>
        </div>
  </div>
</div>  
</div>




<!-- list: {{ items.list }}
city:{{ items.city}}
  -->
</template>
<script setup>
import axios from "axios";
import { ref } from "vue";
//input lat long 
const lati = ref( );
const long = ref( );

const items = ref({});

const apikey = ref("b658e1850340af07649e496a52c67a5f");
//const click = ref(0)




 
// function extractMonth(dt_txt) {
//   const dateParts = dt_txt.split(' ')[0].split('-'); // แยกวันที่ออกมา
//   const year = dateParts[0];
//   const month = dateParts[1];
//   return `${year}-${month}`;
// }<p>Date: {{ extractMonth(items.value.list[index].dt_txt) }}</p>

function fetchPosts() {
const url = ref('https://api.openweathermap.org/data/2.5/forecast?lat='+lati.value+'&lon='+long.value+'&appid='+apikey.value+'&units=metric');
 axios
 .get(url.value)
 .then((response) => {
 items.value = response.data;//สิ่งที่ได้คืนจากฝั่งserver 
 console.log(items.value);
 })
 .catch((err) => {
 console.log(err);
 });
}
//onMounted(fetchPosts);

</script>

<style scoped>
.iconbutton{
max-width: 50px;
}
.subject{
  margin-top: 30px;
  padding: 10px;
  text-align: center;
  font-weight: 500;
  color: #00205B;
  
}

.fixed-top{
    padding: 100px;
    margin-right: 75%;
  }
.card{
padding: 20px;
margin: 20px;

  }
  .card-img{
  padding: 10px;
  margin: 10px;
}
.icontemp{
max-width: 40px;
}
.iconhpa{
max-width: 20px;
}
.list-group{
  margin: 5px;
  padding: 0px;
}
.date{
  color: #222A2E;
}
.text{
  color: #00205B;
}
.borderpurple{
border-color: #AAB3E7;
border-width: 2px;
}
.borderblue{
  border-color: #AAD1E7;
border-width: 2px;
}
</style>