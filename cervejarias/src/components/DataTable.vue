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

    <!-- Modal -->
    <div :class="{ modal:true, fade: true, in: true, 'open-modal': openModal }" id="addBrewery" tabindex="-1" role="dialog" aria-labelledby="Brewery" aria-hidden="true">
      <div class="modal-dialog modal-lg" role="document">
        <div class="modal-content">
          <div class="modal-header">
            <h5 class="modal-title" id="exampleModalLabel">Adicionar Cervejaria</h5>
            <button type="button" class="close" data-dismiss="modal" aria-label="Close">
              <span aria-hidden="true">&times;</span>
            </button>
          </div>
          <div class="modal-body">
            
            <div class="col-lg-12">
                <div class="row">
                    <div class="col-lg-6 form-group">
                        <label class="control-label" for="Name">Name</label>
                        <input type="text" placeholder="Brewery name" id="Name" name="Name" maxlength="255" required="required" 
                                v-model="selected.name" class="form-control">
                    </div>
                    <div class="col-lg-6 form-group">
                        <label class="control-label">Code</label>
                        <input type="text" placeholder="Code" maxlength="5" required="required" v-model="selected.code" class="form-control">
                    </div>
                </div>
                <div class="row">
                    <div class="col-lg-6 form-group">
                        <label class="control-label" >City</label>
                        <input type="text" placeholder="City" maxlength="255" required="required" 
                                v-model="selected.city" class="form-control">
                    </div>
                    <div class="col-lg-6 form-group">
                        <label class="control-label" >State</label>
                        <input type="text" placeholder="State" maxlength="5" required="required" 
                                v-model="selected.state" class="form-control">
                    </div>
                </div>
            </div>

          </div>
          <div class="modal-footer">
            <button type="button" class="btn btn-secondary" data-dismiss="modal">Cancelar</button>
            <button type="button" class="btn btn-primary">Salvar Dados</button>
          </div>
        </div>
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
