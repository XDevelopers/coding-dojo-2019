<template>
    <div>
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
</templat<!-- Modal -->
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
    </div>e>