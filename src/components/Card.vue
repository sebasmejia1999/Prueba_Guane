<template>

    <b-card header-tag="header" class="text-center" style="max-width: 100%; -webkit-box-shadow: 10px 13px 22px -9px rgba(0,0,0,0.75); -moz-box-shadow: 10px 13px 22px -9px rgba(0,0,0,0.75); box-shadow: 10px 13px 22px -9px rgba(0,0,0,0.75);" >
        <template #header>
            <h6 class="mb-0" v-bind:style="{color: color}"><i v-bind:class="icon"></i> <b>{{title}}</b></h6>
        </template>

        <template v-if="type == 'input'">
            <b-row>
                <b-col>
                    <b-form-input v-model="text" placeholder="Enter your name"></b-form-input>
                </b-col>
                <b-col>
                    <b-form-input v-model="text" placeholder="Enter your name"></b-form-input>
                </b-col>
            </b-row>  
        </template>

        <template v-if="type == 'checkbox'" >
            <b-row >
                <b-col cols="1.0"  v-for="item in accesorials" v-bind:key="item" style="margin-right: 40px;">

                    <b-form-checkbox :value="item" >{{item}}</b-form-checkbox>

                </b-col>
            </b-row>
        </template>
    </b-card> 
    
</template>

<script>
export default {
  data : () => ({
    name: 'Card',
    accesorials: ['Hazmat', 'Bonded', 'Tarps', 'Airport Delivery TSA', 'Oversize/Overweight Permits', 'Escorts', 'Team Drivers', 'Non Stackable'],
  }),

  props: {
    title: String,
    color: String,
    icon: String,
    type: String
  }
}
</script>

<style scoped>

</style>