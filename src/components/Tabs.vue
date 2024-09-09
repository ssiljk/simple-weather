<script setup>
import { CTabs, CTabList, CTab, CTabContent, CTabPanel } from '@coreui/vue';
import  Cards  from './Cards.vue';
import { ref } from 'vue';
import '@coreui/coreui/dist/css/coreui.min.css'

</script>

<template>
  <CTabs activeItemKey="angeles">
  <CTabList variant="tabs" layout="justified">
    <CTab itemKey="angeles">LOS ANGELES</CTab>
    <CTab itemKey="beijing">BEIJING</CTab>
    <CTab itemKey="rio">RIO DE JANEIRO</CTab>
    <CTab itemKey ="alianza">CIUDAD ALIANZA</CTab>
  </CTabList>
  <CTabContent>
    <CTabPanel className="py-3" itemKey="angeles">
     <Cards city="5368361" ></Cards>
    </CTabPanel>
    <CTabPanel className="py-3" itemKey="beijing">
        <Cards city="1816670" ></Cards>
    </CTabPanel>
    <CTabPanel className="py-3" itemKey="rio">
        <Cards city="3451190" ></Cards>
    </CTabPanel>
    <CTabPanel className="py-3" itemKey="alianza">
        <Cards city="3625549" ></Cards>
    </CTabPanel>
  </CTabContent>
</CTabs>
</template>
