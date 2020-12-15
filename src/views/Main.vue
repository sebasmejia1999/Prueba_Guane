<template>
    <div style="padding: 30px;">
        <b-row> 
            <b-col cols="6">
                <div> 
                    <Card title="Pick-Up" color="#06CB00" icon="fas fa-map-marker-alt" type="input" :city="city_from" :zip="zip_from"/>
                </div>
            </b-col>
            <b-col cols="6">
                <div> 
                    <Card title="Delivery" color="#FF0808" icon="fas fa-map-marker-alt" type="input" :city="city_to" :zip="zip_to"/>
                </div>
            </b-col>
        </b-row> 

        <b-row style="margin-top:30px"> 
            <b-col cols="12">
                <div> 
                    <Card title="Accesorials" color="#000000" type="checkbox" :accesorials_2="accesorials"/>
                </div>
            </b-col>
        </b-row> 

        <b-row style="margin-top:30px"> 
            <b-col cols="12">
                <div> 
                    <Table :items_prop="items_table" />
                </div>
            </b-col>
        </b-row>
    </div>
    
</template>

<script>
import Card from '../components/Card'
import Table from '../components/Table'
import axios from 'axios'

export default {
  name: 'HelloWorld',

  data : () => ({
    zip_from: "",
    city_from: "",  
    zip_to: "",
    city_to:"",
    accesorials:[],
    items_table:[]
  }),

  props: {
    msg: String
  },

  components: {
    Card, 
    Table
  },

    created: function () { 
        axios.get('https://tt.guane.com.co/api/loads/1').then(response => {
            this.zip_from = response.data.hauls[0].zip_from;
            this.city_from = response.data.hauls[0].city_from;
            this.zip_to = response.data.hauls[0].zip_to;
            this.city_to = response.data.hauls[0].city_to;

            this.accesorials = response.data.hauls[0].accessorials;

            this.items_table = response.data.hauls[0].commodity.map(item => {
                var com = {};
               com['select'] = false;
               com['hu_count'] = item['hu_count'];
               com['dimensions'] = item['dimensions'];
               com['weight'] = item['weight'];
               com['commodity'] = item['commodity'];
               com['stackable'] = false;

               return com;
            }
            );
        }
        ).catch(error => this.errors.push(error));
    }

}
</script>

<style scoped>

</style>