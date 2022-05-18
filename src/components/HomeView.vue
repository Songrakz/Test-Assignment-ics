<template>
  <div class="main">
      <v-container fluid class="container">
          <v-row no-gutters>
              <v-col cols="0" sm="1" md="1" class=".d-none .d-sm-flex">
                
 
              </v-col>
              <v-col cols="12" sm="11" md="11">
                  <div class="all-place">

                        <v-row class="place-search">
                            <v-col cols="12" sm="2" >
                                <p class="place-logo ">Place List</p>
                            </v-col>
                            <v-spacer></v-spacer>
                        <v-col class="res-line " cols="12"  sm="4" >
                    <div class="res-box ">
                      <input type="text" class="res-text" placeholder="Restaurent." />
                      <div class="line"><div class="vl"></div> </div>
                    </div>
                    
                    
                  </v-col >
             
                  <v-col >
                    <div class="name-box">
                      <input type="text" placeholder="Search name..." />
                     
                    </div>
                  </v-col>

                        </v-row>
                        <v-row class="row-place" >
                             <v-col 
                  v-for="place in placeData"
                  :key="place.id"
                  cols="12"
                  md="4"
                  sm="12"
                >
                  <div class="card-place" >
                    <div class="card-header">
                      <img :src="place.profile_image_url" alt="" />
                      <!-- <div class="time-rate"></div> -->
                      <div class="cardheader-right">
                      <!-- <a href="/placeview"><h2>{{ place.name }}</h2></a> -->
                      <router-link class="place-name" :to="{ path: '/placeview', query: { ID: place.id } }"><h2>{{ place.name }}</h2></router-link>

                        <div class="time-rate">
                          <div class="operation-time">
                            <img src="../assets/calendar.svg" alt="" />
                            <p>
                              {{
                                place.operation_time[0].time_open +
                                "AM - " +
                                place.operation_time[0].time_close +
                                "PM"
                              }}
                            </p>
                          </div>
                          <div class="rating-box">
                            <span class="dot"></span>
                            <p>{{place.rating}}</p>
                          </div>
                        </div>
                      </div>
                    </div>
                    <div class="three-img">
                      <v-img
                        :aspect-ratio="16 / 9"
                        class="img-first"
                        :src="place.images[0]"
                        alt=""
                      />
                      <v-img
                        :aspect-ratio="16 / 9"
                        class="img-second"
                        :src="place.images[1]"
                        alt=""
                      />
                      <v-img
                        :aspect-ratio="16 / 9"
                        class="img-third"
                        :src="place.images[2]"
                        alt=""
                      />
                    </div>
                  </div>
                </v-col>
                </v-row>
                <v-row class="page-change">
                           <ul class="selection-group">
          <!-- <span class="pre-page"><i class="arrow left"></i></span>
            <span class="select-page"> <p>1</p></span>
            <span class="next-page"><i class="arrow right"></i></span> -->
          <li>
            <button>
              <span><img src="../assets/previous_btn.svg" alt="" /></span>
            </button>
          </li>
          <li>
            <button>
              <span class="select-page"
                ><img src="../assets/select_btn.svg" alt="" />
                <p>1</p></span
              >
            </button>
          </li>
          <li>
            <button>
              <span class="next-page"
                ><img src="../assets/next_btn.svg" alt=""
              /></span>
            </button>
          </li>
        </ul>
                </v-row>
               
                  </div>
              </v-col>
          </v-row>
          
      </v-container>
  </div>
</template>

<script>
import exampleData from "../assets/example.json";
export default {
  name: "HomePage",
  data() {
    return {
      placeData: exampleData,
    };
  },

  mounted() {
   
  },
};
</script>

<style scoped >
.addb{
    border: solid 2px blue;
}



.empty-space{
    /* border: 2px solid red; */
    width: 90px;
    margin-left: -0.9rem;
}

.all-place{
    /* background-color: red; */
    height: 600px;
    width: 100%;
    /* margin-left: -3rem; */
}



#sidenav {
height: 1456px;
width: 90px;
/* position: fixed; */
position: absolute;
left: 0%;

right: 0%;
top: 0%;
bottom: 0%;
z-index: 2;
background-color: white;
overflow-x: hidden;
padding-top: 10px;
border-radius: 0px 50px 50px 0px;
box-shadow: 0px 10px 10px rgba(0, 0, 0, 0.25);
/* border: red solid 3px; */
margin-top: -5.5rem;
text-align: center;
float:left;
}




/****************************PLACE SEARCH */
.place-logo {
  font-size: 24px;
  font-weight: 500;
  margin-left: 2rem;
}
    

.bell-icon{
  margin-right: 30px;
  margin-top: 5px;
}

.place-name{
  text-decoration: none;
  font-weight: 500;
font-size: 18px;
color: rgba(0, 0, 0, 0.87);
}
.res-box {
  background: #ffffff;
border: 1px solid #134B8A;
  box-sizing: border-box;
  border-radius: 50px;
  display: flex;
  justify-content: space-between;
  /* border: red solid 3px; */
  /* margin-left: 2rem; */
  width: 100%;
 
  /* margin-left: 25px; */
}

.name-box {
  background: #ffffff;
border: 1px solid #134B8A;
  box-sizing: border-box;
  border-radius: 50px;
  display: flex;
  /* justify-content: space-between; */
  /* border: red solid 3px; */
  /* margin-left: 2rem; */
  /* width: 400px; */
  /* margin-left: 25px; */
}
.name-box input {
  color: rgba(0, 0, 0, 0.54);
  font-weight: 400;
  font-size: 14px;
  outline: 0;
    height: 40px;
  width: 400px;
  text-indent: 20px;
}

.res-box input {
  color: rgba(0, 0, 0, 0.54);
  font-weight: 400;
  font-size: 14px;
  outline: 0;
    height: 40px;
  width: 185px;
  text-indent: 20px;
}


/* .res-line{
  display: flex;
} */

.line{
    margin-right: -1rem;
}
.vl {
  border: 1.5px solid #134B8A;
  height: 25px;
  width: 2px;
  margin-left: 14px;
  background: #134B8A;
  margin-top: 0.5rem;
 
}


/**************************MAIN PLACE */
.card-place {
  background-color: #ffff;
  height: 225px;
  width: 400px;
  box-shadow: 0px 3px 3px rgba(0, 0, 0, 0.25);
  border-radius: 10px;
  /* border: solid red 2px; */
}
.card-header {
  display: flex;
}
.card-header img {
  margin-left: 21px;
  margin-top: 17px;
  width: 60px;
  height: 60px;
  border-radius: 10px;
}

.card-header h2 {
  margin-top: 17px;
  font-size: 18px;
  font-weight: 500;
  margin-left: 16px;
  letter-spacing: 0.15px;
}

.three-img {
  margin-top: 11px;
  display: flex;
  margin-left: 17px;
  margin-right: 19px;
  margin-bottom: 17px;
}
.img-first {
  width: 120px;
  height: 120px;
  border-radius: 10px 0px 0px 10px;
}
.img-second {
  width: 120px;
  height: 120px;
}
.img-third {
  width: 120px;
  height: 120px;
  border-radius: 0px 10px 10px 0px;
}

.operation-time {
  display: flex;
  align-items: center;
  margin-left: -0.5rem;
  /* border: red solid 2px; */
}

.operation-time img {
  width: 16.67px;
  height: 15px;
  margin-right: 10px;
  margin-top: -1.2rem;
  margin-right: 5.5px;
}

.operation-time p {
  font-size: 14px;
  font-weight: 400;
  letter-spacing: 0.15px;
  color: rgba(0, 0, 0, 0.87);
}

.rating-box span {
  margin-left: 96px;
  height: 11px;
  width: 11px;
  background-color: #134b8a;
  border-radius: 50%;
  display: inline-block;
  margin-top: -1rem;
}

.rating-box {
  display: flex;
  align-items: center;
}

.rating-box p {
  font-size: 16px;
  font-weight: 500;
  letter-spacing: 0.15px;
  color: #134b8a;
  margin-left: 7px;
}

.time-rate {
  display: flex;
}

.row-place{
    
    width: 1305px;
}


/*****SELECTION PAGE */
.selection-group {
  /* border: red solid 2px; */
  margin-left: 6rem;
  width: 1250px;
  display: flex;
  justify-content: center;
  margin-top: 53px;
}
.selection-group li {
  margin-right: 36px;
  list-style: none;
}

.arrow {
  border: solid #9e9e9e;
  border-width: 0 1.5px 1.5px 0;
  display: inline-block;
  padding: 3px;
  margin-top: 1rem;
  margin-left: 1rem;
}
.left {
  transform: rotate(135deg);
  -webkit-transform: rotate(135deg);
}

.right {
  transform: rotate(-45deg);
  -webkit-transform: rotate(-45deg);
}

.select-page p {
  font-size: 16px;
  font-weight: 500;
  letter-spacing: 0.15px;
  color: #ffffff;
  margin-top: -2.4rem;
}


</style>


