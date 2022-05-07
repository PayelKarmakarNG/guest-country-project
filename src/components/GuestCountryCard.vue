<template>
  <div style="height:100vh" 
      dense
      class="d-flex flex-column justify-center align-center">
      <v-card width="394"
              height="304"
      >
        <v-card-title class="heading">
            Guest Country
        </v-card-title>

        <v-divider />

        <v-card-text 
          class="country-list" 
          v-if="guestCountryData">
          <div 
              v-for="elem in guestCountryData" 
              :key="elem.id"
              class="country-details">
              <v-row>
                <v-col cols="8">
                  {{ countryCode[elem.display_code] }}
                </v-col>
                <v-col 
                  cols="2"
                  class="pl-2">
                  {{ elem.nr_of_rooms }}
                </v-col>
                <v-col 
                  cols="2"
                  class="pl-0 ml-0 shift-left"
                  :class="elem.changeInValue > 0 ? 'green--text' : 'red--text'">
                  {{ elem.changeInValue }}
                </v-col>
              </v-row>
              <v-row class="progress-bar-row">
                <v-col 
                  cols="9"
                  class="mt-2">
                  <v-progress-linear
                    :value="elem.nr_of_rooms/progressBarMaxValue*100"
                    color="#035086"
                    rounded
                    height="8"
                ></v-progress-linear>
                </v-col>
                <v-col 
                  cols="3"
                  class="pl-0"
                  style="font-size: 10px">
                  vs. Last Year
                </v-col>
              </v-row>
          </div>

        </v-card-text>
      </v-card>
    </div>
</template>

<script>
import axios from 'axios'
import { COUNTRY_CODE_MAPPING } from '../country-mapping'

export default {
    name: 'GuestCountryCard',
    data() {
        return {
          guestCountryData: null,
          countryCode: COUNTRY_CODE_MAPPING,
        }
    },

    async created () {
        const response = await axios.get('https://data.otainsight.com/public-data/frontend-hiring/guest-country-sample.json')
        this.guestCountryData = response.data.guest_country
          .map(elem => {
            return {
              id: elem.id,
              display_code: elem.display_code,
              nr_of_rooms: elem.value.nr_of_rooms,
              changeInValue: (elem.value.nr_of_rooms - elem.reference_value.nr_of_rooms) > 0 ?
                '+' + (elem.value.nr_of_rooms - elem.reference_value.nr_of_rooms) : elem.value.nr_of_rooms - elem.reference_value.nr_of_rooms
            }
          })
          .sort((a, b) => b.nr_of_rooms - a.nr_of_rooms)
          .sort((a, b) => b.changeInValue - a.changeInValue)
    },
    
    computed: {
      progressBarMaxValue() {
        const value_array = []
        this.guestCountryData.forEach(elem => {
          value_array.push(elem.nr_of_rooms)
        })
        return Math.max(...value_array)
      }
    }
}
</script>


<style scoped>
  .heading {
    font-size: 12px;
    font-weight: 700;
    line-height: 20px;
    position: relative;
    height: 44px;
    bottom: 5px;
    border-radius: 4px 4px 0px 0px;
  }
  .country-details {
    font-size: 12px;
    position: relative;
    height: 52px;
    right: 18px;
    bottom: 16px;
    width: 394px;
    padding-left: 16px;
    padding-top: 8px;
    color: #4E6477;
    border-bottom: 1px solid #E5E5E5;
  }
  .country-list {
    max-height: 260px;
    overflow-y: scroll;
    overflow-x: hidden;
  }
  .text-body-3 {
    position: relative;
    right: 10px;
  }
  .progress-bar-row{
    position: relative;
    bottom: 25px;
  }
  .shift-left{
    position: relative;
    right: 31px;
  }
</style>