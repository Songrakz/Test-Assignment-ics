<template>
  <div>
    <v-row width="100%" class="mr-5 ml-5 mt-3">
      <v-col cols="12" sm="7">
        <h2 class="text1">Place list</h2>
      </v-col>
      <v-col cols="12" sm="2">
        <v-select
          :items="items"
          v-model="select"
          item-text="text"
          item-value="value"
          @change="getCategories"
          label="Restaurant"
          heigth="40px"
          chips
          clearable
          hide-details
          hide-selected
          rounded
          class="select"
        ></v-select>
      </v-col>
      <v-divider vertical class="divider d-none d-sm-flex"></v-divider>
      <v-col cols="12" sm="3">
        <v-text-field
          v-model="keyword"
          heigth="40px"
          append-icon="search"
          style="padding: 10px;"
          chips
          clearable
          hide-details
          hide-selected
          label="Search name..."
          rounded
          class="select"
          @keyup="searchPlace"
          @click:clear="resetData"
        ></v-text-field>
      </v-col>
    </v-row>

    <v-container fluid grid-list-lg class="con">
      <div class="row_card d-none d-sm-flex"></div>
      <v-layout row wrap>
        <v-flex v-for="placedata in placedatas" :key="placedata">
          <v-card class="card" style="border-radius: 10px">
            <v-container>
              <v-row>
                <v-col cols="3">
                  <v-img
                    :src="placedata.profile_image_url"
                    width="60px"
                    height="60px"
                  ></v-img>
                </v-col>
                <v-col>
                  <h2 class="text2">{{ placedata.name }}</h2>
                  <div class="con mt-2">
                    <v-icon color="black">calendar_month</v-icon>
                    <h2 class="text3 ml-1">
                      {{
                        placedata.operation_time[0].time_open +
                        "AM -" +
                        placedata.operation_time[0].time_close +
                        "PM"
                      }}
                    </h2>
                    <v-spacer></v-spacer>
                    <span class="dot"></span>
                    <h2 class="text4 ml-2">{{ placedata.rating }}</h2>
                  </div>
                </v-col>
              </v-row>
            </v-container>
            <v-container class="conimg">
              <v-img
                :src="placedata.images[0]"
                width="120px"
                height="120px"
                style="border-radius: 10px 0px 0px 10px"
              ></v-img>
              <v-img
                :src="placedata.images[1]"
                width="120px"
                height="120px"
              ></v-img>
              <v-img
                :src="placedata.images[2]"
                width="120px"
                height="120px"
                style="border-radius: 0px 10px 10px 0px"
              ></v-img>
            </v-container>
          </v-card>
        </v-flex>
      </v-layout>
    </v-container>
  </div>
</template>

<script>
// @ is an alias to /src

import Sidebar from "@/components/Sidebar.vue";
import example_data from "@/assets/example_data.json";
export default {
  name: "HomeView",
  components: {
    Sidebar,
  },
  data() {
    return {
      items: [
        { value: "restaurant", text: "Restaurant" },
        { value: "cafe", text: "Cafe" },
        { value: "bakery", text: "Bakery" },
      ],
      placedatas: example_data,
      select: '',
      keyword: '',
    };
  },

  methods: {
    getCategories() {
      if (!this.select) {
        this.resetData();
        return 
      }
      this.resetData();
      const temp = this.placedatas.filter((item) => {
        if (item.categories.includes(this.select)) {
          return item;
        }
      });
      this.placedatas = temp;
      console.log(temp); 
    },
    searchPlace() {
      if (!this.keyword) {
        this.resetData();
        return 
      }
      this.resetData();
      const temp = this.placedatas.filter((item) => {
        if (item.name.toLowerCase().includes(this.keyword.toLowerCase())) {
          return item;
        }
      });
      this.placedatas = temp;
    },
    resetData() {
      this.placedatas = example_data;
    }
  },

  mounted() {
    console.log(this.items);
  },
};
</script>

<style scoped>
.text1 {
  font-weight: 500;
  margin-left: 90px;
}
.text2 {
  font-weight: 500;
  font-size: 18px;
}
.text3 {
  font-weight: 500;
  font-size: 14px;
}
.text4 {
  font-weight: 500;
  font-size: 16px;
  color: #134b8a;
}
.con {
  display: flex;
}
.conimg {
  display: flex;
}
.row_card {
  margin-left: 120px;
}
.card {
  width: 400px;
  height: 225px;
}
.divider {
  background-color: #134b8a;
  height: 40px;
  margin-top: 25px;
}
.select {
  border: #134b8a solid;
}
.dot {
  height: 11px;
  width: 11px;
  background-color: #134b8a;
  border-radius: 50%;
  margin-top: 5px;
}
.b {
  border: red solid;
}
</style>
