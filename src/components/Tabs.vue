<script setup>
import { CTabs, CTabList, CTab, CTabContent, CTabPanel } from '@coreui/vue';
import  Cards  from './Cards.vue';
import { Place } from '../classes/Place.js';
import { ref } from 'vue';
import '@coreui/coreui/dist/css/coreui.min.css'

const cities = [];

const city1 = new Place(5368361, "Los Angeles", -8);
const city2 = new Place(1816670, "Beijing", 8);
const city3 = new Place(3451190, "Rio de Janeiro", -3);
const city4 = new Place(3448439, "Ciudad Alianza", -3);
cities.push(city1, city2, city3, city4);

console.log("cities:", cities);

</script>

<template>
  <div>
    <CTabs activeItemKey= "{{cities[0].id}}">
    <CTabList variant="tabs" layout="justified">
      <CTab itemKey="{{ cities[0].id }}">{{cities[0].name}}</CTab>
      <CTab itemKey="{{ cities[1].id }}">{{cities[1].name}}</CTab>
      <CTab itemKey="{{ cities[2].id }}">{{cities[2].name}}</CTab>
      <CTab itemKey="{{ cities[3].id }}">{{cities[3].name}}</CTab>
    </CTabList>
    <CTabContent>
      <CTabPanel  className="py-3" itemKey="{{ cities[0].id }}">
        <Cards :city="cities[0]"></Cards>
      </CTabPanel>
      <CTabPanel  className="py-3" itemKey="{{ cities[1].id }}">
        <Cards :city="cities[1]"></Cards>
      </CTabPanel>
      <CTabPanel  className="py-3" itemKey="{{ cities[2].id }}">
        <Cards :city="cities[2]"></Cards>
      </CTabPanel> 
      <CTabPanel  className="py-3" itemKey="{{ cities[3].id }}">
        <Cards :city="cities[3]"></Cards>
      </CTabPanel> 
      <!-- <CTabPanel className="py-3" itemKey="beijing">
          <Cards city="1816670" ></Cards>
      </CTabPanel>
      <CTabPanel className="py-3" itemKey="rio">
          <Cards city="3451190" ></Cards>
      </CTabPanel>
      <CTabPanel className="py-3" itemKey="alianza">
          <Cards city="3625549" ></Cards>
      </CTabPanel>  -->
    </CTabContent>
   </CTabs>
  </div>
</template>
