<template>
    <b-row>
    
        <b-col cols="12">
            <div style="background-color: #071630; height: 100% ; border-top-left-radius: 10px; border-top-right-radius:10px;">
            <b-button variant="primary" style="margin-right:10px; float: left; margin:10px;" v-on:click="remove()">Delete</b-button>
            <b-button variant="primary" style="margin-left:10px; float: left;  margin:10px;" v-on:click="addRow()">Add new row</b-button>

            <b-row style="padding:10px">
                <b-col cols="2">
                    <b-form-input v-model="data_row.hu_count" placeholder="Hu count" style="float:left"></b-form-input>
                </b-col>
                <b-col cols="2">
                    <b-form-input v-model="data_row.dimensions" placeholder="Dimensions" style="float:left"></b-form-input>
                </b-col>
                <b-col cols="2">
                    <b-form-input v-model="data_row.weight" placeholder="Weight" style="float:left"></b-form-input>
                </b-col>
                <b-col cols="2">
                    <b-form-input v-model="data_row.commodity" placeholder="Commodity" style="float:left"></b-form-input>
                </b-col>
                <b-col cols="2">
                    <b-form-checkbox v-model="data_row.stackable" name="check-button" switch><b style="color:white">Stackable</b></b-form-checkbox>
                </b-col>
            </b-row>
            
            </div>

        </b-col>

        <b-col cols="12">

            <b-table striped hover :items="items_prop" bordered style="widht:100%">

            <template #cell(select)="data">
                <b-form-checkbox
                :id="data.index.toString()"
                :v-model="items_remove"
                :value="data.select"
                :unchecked-value="false"
                @change="select_remove(data)"
                >
              </b-form-checkbox>
            </template>

            <template #cell(stackable)="data">
                <b-form-checkbox :v-model="data.stackable" :value="data.stackable" name="check-button" switch>
    
                </b-form-checkbox>
            </template>

            </b-table>

        </b-col>
        
    </b-row>
    

</template>

<script>
export default {
  data : () => ({
      items: [],
      data_row: {
          select: false,
          hu_count: "",
          dimensions: "",
          weight: "",
          commodity: "",
          stackable: false
      },

      items_remove:[]
  }),

  methods: {
        addRow(){
          this.items_prop.push(Object.assign({} , this.data_row));
          this.data_row.hu_count = "";
          this.data_row.dimensions = "";
          this.data_row.weight = "";
          this.data_row.commodity = "";
        },

        select_remove(data){

            var index = this.items_remove.indexOf(data.index);

            if(index == -1){
                this.items_remove.push(data.index);
            }else if(index > -1){
                this.items_remove.splice(index, 1);
            }
        },

        remove(){

            for (let index = 0; index < this.items_remove.length; index++) {
                this.items_prop[this.items_remove[index]] = null;
            }
            this.items_prop = this.items_prop.filter(Boolean);
            this.items_remove= [];
        }
  },

  props: {
      items_prop: Array
  }
}
</script>

<style scoped>

</style>