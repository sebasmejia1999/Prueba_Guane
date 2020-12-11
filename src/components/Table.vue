<template>
    <b-row>
    
        <b-col cols="12">
            <div style="background-color: #071630; height: 100% ; border-top-left-radius: 10px; border-top-right-radius:10px;">
            <b-button variant="primary" style="margin-right:10px; float: left; margin:10px;">Delete</b-button>
            <b-button variant="primary" style="margin-left:10px; float: left;  margin:10px;">Add new row</b-button>
            </div>
        </b-col>

        <b-col cols="12">

            <b-table striped hover :items="items" bordered style="widht:100%"></b-table>

        </b-col>
        
    </b-row>
    

</template>

<script>
export default {
  data : () => ({
      items: [
          { age: 40, first_name: 'Dickerson', last_name: 'Macdonald' },
          { age: 21, first_name: 'Larsen', last_name: 'Shaw' },
          { age: 89, first_name: 'Geneva', last_name: 'Wilson' },
          { age: 38, first_name: 'Jami', last_name: 'Carney' }
        ]
  }),

  props: {

  }
}
</script>

<style scoped>

</style>