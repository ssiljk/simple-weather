<script setup>
import { ref } from 'vue';
import { CRow, CCol } from '@coreui/vue'
import Card from './Card.vue';
import axios from 'axios';
import { reactive, onMounted } from 'vue';
import '@coreui/coreui/dist/css/coreui.min.css'
import { Place } from '@/classes/Place';
const props = defineProps({
    city: Place
})
console.log("props.city:", props.city);

const state = reactive({
    response: Object,
    isLoading: true,
});

onMounted(async () => {
    try {
        const responseString = await axios.get("http://api.openweathermap.org/data/2.5/forecast?id="+props.city.id+"&appid=ab9f7ca8b3c79eb846a5cc344487cb06&cnt=5&units=metric");
     
        state.response = responseString.data;

        for (var i = 0; i < state.response.list.length; i++) {  
           state.response.list[i].weather[0].icon = "https://openweathermap.org/img/wn/" + state.response.list[i].weather[0].icon + "@2x.png";
           console.log("list: ", state.response.list[i]);      
        }

    } catch (error) {
        console.error('Error fetching data', error);
    } finally {
        state.isLoading = false;
    }
});

function formatDate(unix_timestamp, offset) {
    console.log("offset:", offset);
    console.log("unix_timestamp:", unix_timestamp);
    var hours = new Date(unix_timestamp * 1000 + offset * 3600 * 1000).getHours(); 
    console.log("hours:", hours);
    if(hours < 12) {
        return hours + " AM";
    }  
    else {
        return hours - 12 + " PM";  

    }
}

</script>

 <template>
   
        <tr>
            <Card v-for="point in state.response.list" :temp="point.main.temp" :humidity="point.main.humidity"
                :icon="point.weather[0].icon" :hour="formatDate(point.dt,props.city.utcOffset)"></Card>
        </tr>
   
</template> 


