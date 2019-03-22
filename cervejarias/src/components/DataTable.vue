<template>
  <div class="container-fluid">
    <h1>{{ msg }}</h1>
    <h3>Cervejarias</h3>
    <br />
    <div class="row">
      <div class="col-md-10 mx-auto">
        <div class="text-left">
          <!-- Button trigger modal -->
          <button type="button" class="btn btn-primary" data-toggle="modal" data-target="#addBrewery">
            Adicionar Cervejaria
          </button>
        </div>
      </div>
    </div>
    
    <div class="row">
      <div class="col-md-10 mx-auto">        
        <table class="table table-bordered table-responsive">
          <thead>
            <tr>
              <th>Name</th>
              <th>City</th>
              <th>State</th>
              <th>Phone</th>
              <th>Actions</th>
            </tr>
          </thead>
          <tr v-for="brewery in breweries" :key="brewery.id">
            <td>{{ brewery.name }}</td>
            <td>{{ brewery.city }}</td>
            <td>{{ brewery.state }}</td>
            <td>{{ brewery.phone }}</td>
            <td> Edit | Delete </td>
          </tr>
        </table>
      </div>
    </div>

  </div>
</template>

<script>
import axios from 'axios';
import Modal from '@/components/Modal';
export default {
  name: "DataTable",
  components: {
    Modal
  },
  props: {
    msg: String
  },
  data () {
    return {
      breweries: [],
      selected: {},
      search: '',
      openModal: false,
    }
  },
  mounted () {
    this.loadBreweries();
  },
  methods: {
    loadBreweries(){
      axios
      .get('https://raw.githubusercontent.com/XDevelopers/coding-dojo-2019/master/cervejarias.json')
      .then(response => 
      {
        this.breweries = response.data.breweries;
        //console.log(this.result.breweries);
      });
    },
    newBrewery(){
      this.selected = {};
      this.openModal = true;
    },
    editBrewery(brewery){
      this.selected = brewery;
      this.openModal = true;
    },
    saveBrewery(){
        if (this.selected.id != null){  
          //EDIT
          axios.put(`/breweries/${this.selected.id}`, this.selected)
          .then(
            response=>{
              this.$set('selected',{})
              this.$set('openModal',false)
            },
            error=>{
              console.error(error)
            }
          )
          .finally(
            this.loadBreweries()
          )
          }
          else
          { 
            //NEW
            this.$http.post(`/breweries`,this.selected).then(
            response=>{
              this.$set('selected',{})
              this.$set('openModal',false)
            },
            error=>{
              console.error(error)
            }
            ).finally(
              this.loadBreweries()
            )
          }
       },
       removeBrewery(brewery){
        let self = this;
        // SweetAlert == sweetalert
        // swal({  title: "Você tem certeza?",
        //         text: `Deseja apagar "${brewery.name}"`,   
        //         type: "warning",   
        //         showCancelButton: true,   
        //         confirmButtonColor: "#DD6B55",   
        //         cancelButtonText: "Cancelar",
        //         confirmButtonText: "Sim, pode apagar!", 
        //         showLoaderOnConfirm: true,  
        //         closeOnConfirm: false }, function(){   
                
        //         self.$http.delete(`/breweries/${brewery.id}`).then(
        //           result=>{
        //             swal("Cervejaria removida!")
        //             self.loadBreweries()
        //           })
        // });

       },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
.table tr td {
  text-align: left;
}
.row {
  margin: 0px 0px 20px 0px;
}
.modal-body {
  text-align: left;
}
</style>
