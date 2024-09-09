<script setup>
import { CCard, CCardImage, CCardBody, CCardTitle, CCardText, CButton } from '@coreui/vue';

import '@coreui/coreui/dist/css/coreui.min.css'

const props = defineProps({
    temp: Number,
    humidity: Number,
    icon: String,
    hour: String
})

</script>

<template>  
<CCard style="width: 25%">
  <CCardBody>
    <CCardTitle>{{ props.temp }} °C</CCardTitle>
    <CCardText>{{ props.humidity }} %</CCardText>
    <CCardImage orientation="bottom" :src="icon" />
    <CCardText>{{ props.hour }}</CCardText>
  </CCardBody>
</CCard>
</template>
