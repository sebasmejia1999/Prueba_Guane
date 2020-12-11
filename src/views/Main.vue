<template>
    <div style="padding: 30px;">
        <b-row> 
            <b-col cols="6">
                <div> 
                    <Card title="Pick-Up" color="#06CB00" icon="fas fa-map-marker-alt" type="input"/>
                </div>
            </b-col>
            <b-col cols="6">
                <div> 
                    <Card title="Delivery" color="#FF0808" icon="fas fa-map-marker-alt" type="input"/>
                </div>
            </b-col>
        </b-row> 

        <b-row style="margin-top:30px"> 
            <b-col cols="12">
                <div> 
                    <Card title="Accesorials" color="#000000" type="checkbox"/>
                </div>
            </b-col>
        </b-row> 

        <b-row style="margin-top:30px"> 
            <b-col cols="12">
                <div> 
                    <Table />
                </div>
            </b-col>
        </b-row>
    </div>
    
</template>

<script>
import Card from '../components/Card'
import Table from '../components/Table'

export default {
  name: 'HelloWorld',

  props: {
    msg: String
  },

  components: {
    Card, 
    Table
  }
}
</script>

<style scoped>

</style>