<template>
    <b-container fluid>
      <b-modal id="modal-1" ref="modal-1" size="xl" title="Nuevo Alumno">
        <form>
          <div class="col-md-12 mb-3">
            <label for="nit">Nit</label>
            <input
              required
              type="text"
              class="form-control"
              id="nit"
              v-model.trim="$v.form.nitPropietario.$model"
              :state="!$v.form.nitPropietario.$error"
              placeholder="Ingresar nit"
          >
          </div>
          <div class="col-md-12 mb-3">
            <label for="cui">CUI</label>
            <input
              required
              class="form-control"
              id="cui"
              v-model.trim="$v.form.cuiPropietario.$model"
              :state="!$v.form.cuiPropietario.$error"
              placeholder="Ingresar cui"
            >
          </div>
          <div class="col-md-12 mb-3">
            <label for="nombre">Nombre Del Propietario</label>
            <input
              required
              class="form-control"
              id="nombre"
              v-model.trim="$v.form.nombrePropietario.$model"
              :state="!$v.form.nombrePropietario.$error"
              placeholder="nombre"
            >
          </div>
          <div class="col-md-12 mb-3">
            <label for="tipo">Tipo</label>
            <input
              required
              class="form-control"
              id="tipo"
              v-model.trim="$v.form.tipo.$model"
              :state="!$v.form.tipo.$error"
              placeholder="Ingresar el Tipo del vehiculo"
            >
          </div>
          <div class="col-md-12 mb-3">
            <label for="marca">Marca</label>
            <input
              required
              class="form-control"
              id="marca"
              v-model.trim="$v.form.marca.$model"
              :state="!$v.form.marca.$error"
              placeholder="Ingresar marca de vehiculo"
            >
          </div>
          <div class="col-md-12 mb-3">
            <label for="linea">Linea</label>
            <input
              required
              class="form-control"
              id="linea"
              v-model.trim="$v.form.linea.$model"
              :state="!$v.form.linea.$error"
              placeholder="Ingresar linea del vehiculo"
            >
          </div>
          <div class="col-md-12 mb-3">
            <label for="modelo">Modelo</label>
            <input
              required
              class="form-control"
              id="modelo"
              v-model.trim="$v.form.modelo.$model"
              :state="!$v.form.modelo.$error"
              placeholder="Ingresar Modelo del vehiculo"
            >
          </div>
          <div class="col-md-12 mb-3">
            <label for="placa">Placa</label>
            <input
              required
              class="form-control"
              id="placa"
              v-model.trim="$v.form.placa.$model"
              :state="!$v.form.placa.$error"
              placeholder="Ingresar placa del vehiculo"
            >
          </div>
          <div class="col-md-12 mb-3">
            <label for="vin">Vin</label>
            <input
              required
              class="form-control"
              id="vin"
              v-model.trim="$v.form.vin.$model"
              :state="!$v.form.vin.$error"
              placeholder="Ingresar vin del vehiculo"
            >
          </div>
          <div class="col-md-12 mb-3">
            <label for="chasis">Chasis</label>
            <input
              required
              class="form-control"
              id="chasis"
              v-model.trim="$v.form.chasis.$model"
              :state="!$v.form.chasis.$error"
              placeholder="Ingresar chasis del vehiculo"
            >
          </div>
          <div class="col-md-12 mb-3">
            <label for="color">Color</label>
            <input
              required
              class="form-control"
              id="color"
              v-model.trim="$v.form.color.$model"
              :state="!$v.form.color.$error"
              placeholder="Ingresar color del vehiculo"
            >
          </div>
        </form>
        <template #modal-footer="{}">
          <b-button  variant="primary" @click="onSave()"
            >Crear Vehiculo</b-button
          >
          <b-button variant="danger" @click="closeModal('save')"
            >Cancelar</b-button
          >
        </template>
      </b-modal>
      <b-modal id="modal-2" ref="modal-2" title="Editar Vehiculo">
        <form>
          <div class="col-md-12 mb-3">
            <label for="nitPropietario">Nit</label>
            <input
              required
              type="text"
              class="form-control"
              id="nitPropietario"
              v-model.trim="$v.form.nitPropietario.$model"
              :state="!$v.form.nitPropietario.$error"
          >
          </div>
          <div class="col-md-12 mb-3">
            <label for="cuiPropietario">CUI</label>
            <input
              required
              class="form-control"
              id="cuiPropietario"
              v-model.trim="$v.form.cuiPropietario.$model"
              :state="!$v.form.cuiPropietario.$error"
            >
          </div>
          <div class="col-md-12 mb-3">
            <label for="nombrePropietario">Nombre Del Propietario</label>
            <input
              required
              class="form-control"
              id="nombrePropietario"
              v-model.trim="$v.form.nombrePropietario.$model"
              :state="!$v.form.nombrePropietario.$error"
            >
          </div>
          <div class="col-md-12 mb-3">
            <label for="tipo">Tipo</label>
            <input
              required
              class="form-control"
              id="tipo"
              v-model.trim="$v.form.tipo.$model"
              :state="!$v.form.tipo.$error"
            >
          </div>
          <div class="col-md-12 mb-3">
            <label for="marca">Marca</label>
            <input
              required
              class="form-control"
              id="marca"
              v-model.trim="$v.form.marca.$model"
              :state="!$v.form.marca.$error"
            >
          </div>
          <div class="col-md-12 mb-3">
            <label for="linea">Linea</label>
            <input
              required
              class="form-control"
              id="linea"
              v-model.trim="$v.form.linea.$model"
              :state="!$v.form.linea.$error"
            >
          </div>
          <div class="col-md-12 mb-3">
            <label for="modelo">Modelo</label>
            <input
              required
              class="form-control"
              id="modelo"
              v-model.trim="$v.form.modelo.$model"
              :state="!$v.form.modelo.$error"
            >
          </div>
          <div class="col-md-12 mb-3">
            <label for="placa">Placa</label>
            <input
              required
              class="form-control"
              id="placa"
              v-model.trim="$v.form.placa.$model"
              :state="!$v.form.placa.$error"
            >
          </div>
          <div class="col-md-12 mb-3">
            <label for="vin">Vin</label>
            <input
              required
              class="form-control"
              id="vin"
              v-model.trim="$v.form.vin.$model"
              :state="!$v.form.vin.$error"
            >
          </div>
          <div class="col-md-12 mb-3">
            <label for="chasis">Chasis</label>
            <input
              required
              class="form-control"
              id="chasis"
              v-model.trim="$v.form.chasis.$model"
              :state="!$v.form.chasis.$error"
            >
          </div>
          <div class="col-md-12 mb-3">
            <label for="color">Color</label>
            <input
              required
              class="form-control"
              id="color"
              v-model.trim="$v.form.color.$model"
              :state="!$v.form.color.$error"
            >
          </div>
        </form>
        <template #modal-footer="{}">
          <b-button  variant="primary" @click="onState()"
            >Editar Vehiculo</b-button
          >
          <b-button variant="danger" @click="closeModal('update')"
            >Cancelar</b-button
          >
        </template>
      </b-modal>
      <b-modal id="modal-3" ref="modal-3" title="Eliminar Vehiculo">
        <h6 class="my-4">
          Desea eliminar el siguiente vehiculo: <br>
          Propietario: {{ form.nombrePropietario }} <br>
          Marca: {{ form.marca }} <br>
          Linea: {{ form.linea }} <br>
          Modelo: {{ form.modelo }} <br>
          Placa: {{ form.placa }}
        </h6>
        <template #modal-footer="{}">
          <b-button
            type="submit"
            variant="primary"
            @click="DeleteData ()
                    $bvModal.hide('modal-3')"
            >Borrar</b-button
          >
          <b-button variant="danger" @click="$bvModal.hide('modal-3')"
            >Cancelar</b-button
          >
        </template>
      </b-modal>
      <b-modal id="modal-4" ref="modal-4" title="Activar post">
        <h6 class="my-4">
          ¿Desea activar el post: {{ form.nombre }} ?
        </h6>
        <template #modal-footer="{}">
          <b-button
            type="submit"
            variant="primary"
            @click="onState()
                    $bvModal.hide('modal-4')"
            >Activar</b-button
          >
          <b-button variant="danger" @click="$bvModal.hide('modal-4')"
            >Cancelar</b-button
          >
        </template>
      </b-modal>
      <b-row>
        <b-col md="12">
          <iq-card>
              <template v-slot:headerTitle>
                <h4 class="card-title mt-3">Alumnos</h4>
                <div class="iq-search-bar mt-2">
                  <div class="row">
                    <div class="col-sm">
                      <b-form action="#" class="searchbox">
                          <b-input id="search" placeholder="Buscar..." @input="(val) => searchChange(val)" />
                          <a class="search-link" href="#"><i class="ri-search-line"></i></a>
                      </b-form>
                    </div>
                  </div>
                </div>
              </template>
              <template v-slot:headerAction>
              <b-button variant="primary"  v-b-modal.modal-1>AGREGAR NUEVO</b-button>
            </template>
            <template v-slot:body>
              <table class="table table-striped custom-table mb-0">
                  <thead>
                      <th>
                          NIT
                      </th>
                      <th>
                          CUI
                      </th>
                      <th>
                          Nombre
                      </th>
                      <th>
                          Tipo
                      </th>
                      <th>
                          Marca
                      </th>
                      <th>
                          Linea
                      </th>
                      <th>
                          Modelo
                      </th>
                      <th>
                          Placa
                      </th>
                      <th>
                          Vin
                      </th>
                      <th>
                          Chasis
                      </th>
                      <th>
                          Color
                      </th>
                      <th>
                          Accion
                      </th>
                  </thead>
                  <tbody>
                      <tr v-for="datos in datosPosts" :key="datos.id">
                          <td v-text="datos.nitPropietario"></td>
                          <td v-text="datos.cuiPropietario"></td>
                          <td v-text="datos.nombrePropietario"></td>
                          <td v-text="datos.tipo"></td>
                          <td v-text="datos.marca"></td>
                          <td v-text="datos.linea"></td>
                          <td v-text="datos.modelo"></td>
                          <td v-text="datos.placa"></td>
                          <td v-text="datos.vin"></td>
                          <td v-text="datos.chasis"></td>
                          <td v-text="datos.color"></td>
                          <td>
                            <a class="px-2 edit" @click="openModal('update', datos.id)"><i class="fas fa-edit fa-lg"></i></a>
                            <a class="px-2 edit" @click="openModal('delete',datos.id)"><i class="fas fa-trash-alt fa-lg"></i></a>
                          </td>
                      </tr>
                  </tbody>
              </table>
            </template>
          </iq-card>
        </b-col>
      </b-row>
    </b-container>
  </template>
<script>
import { xray } from '../../../config/pluginInit'
// import VuetablePagination from 'vuetable-2/src/components/VuetablePagination.vue'
import useVuelidate from '@vuelidate/core'
import { required } from '@vuelidate/validators'
import axios from 'axios'
import { apiUrl, laravelUrl } from '../../../config/constant'
export default {
  name: 'Vehiculos',
  components: {
  },
  setup () {
    return { $v: useVuelidate() }
  },
  mounted () {
    xray.index()
    axios.get(apiUrl + '/type/get').then((response) => {
      this.typeOptions = response.data
    })
    this.getDatos()
    console.log('Aqui ya esta montado el componente')
    },
    beforeDestroy () {
      // vacio
      this.mensajeDespedida()
    },
    beforeMount () {
      console.log('Aqui empieza el componente')
    },
    data () {
      return {
        from: 0,
        to: 0,
        total: 0,
        perPage: 5,
        search: '',
        datosPosts: [],
        form: {
          id: 0,
          nitPropietario: '',
          cuiPropietario: '',
          nombrePropietario: '',
          tipo: '',
          marca: '',
          linea: '',
          modelo: '',
          placa: '',
          vin: '',
          chasis: '',
          color: ''
        },
        apiBase: laravelUrl + '/api/vehiculo/get/',
        typeOptions: [],
        options: [
          { value: '1', nombre: 'Nombre' },
          { value: '2', nombre: 'Universidad' },
          { value: '3', nombre: 'Carrera' }
        ],
        columna: { value: '1', nombre: 'Nombre' },
        fields: [
          {
            name: 'nombre',
            sortField: 'nombre',
            title: 'Nombre',
            dataClass: 'list-item-heading'
          },
          {
            name: 'universidad',
            sortField: 'universidad',
            title: 'Universidad',
            dataClass: 'list-item-heading'
          },
          {
            name: 'carrera',
            sortField: 'carrera',
            title: 'Carrera',
            dataClass: 'list-item-heading'
          },
          {
            name: '__slot:actions',
            title: 'Acciones',
            titleClass: '',
            dataClass: 'text-muted'
            // width: "15%",
          }
        ]
      }
    },
    validations () {
      return {
        form: {
          nitPropietario: { required },
          cuiPropietario: { required },
          nombrePropietario: { required },
          tipo: { required },
          marca: { required },
          linea: { required },
          modelo: { required },
          placa: { required },
          vin: { required },
          chasis: { required },
          color: { required }
        }
      }
    },
    methods: {
      getDatos () {
        axios.get(laravelUrl + '/api/vehiculo/get').then((response) => {
          this.datosPosts = response.data
          console.log(this.datosPosts)
        })
      },
      postEstado (accion, datos) {
        this.form.nombre = datos.nombre
        this.form.state = datos.completed
        this.form.id = datos.id
        if (accion === 1) {
          this.mensaje('Este post esta completo')
          this.$refs['modal-3'].show()
        } else if (accion === 2) {
          this.mensaje('Este post esta incompleto')
          this.$refs['modal-4'].show()
        }
      },
      openModal (modal, id) {
        switch (modal) {
          case 'save': {
            this.$v.$reset()
            this.form.id = 0
            this.form.nitPropietario = ''
            this.form.cuiPropietario = ''
            this.form.nombrePropietario = ''
            this.form.tipo = ''
            this.form.marca = ''
            this.form.linea = ''
            this.form.modelo = ''
            this.form.placa = ''
            this.form.vin = ''
            this.form.chasis = ''
            this.form.color = ''
            break
          }
          case 'update': {
            const datoAEditar = this.datosPosts.find(dato => dato.id === id)
            if (datoAEditar) {
              this.form.id = datoAEditar.id
              this.form.nitPropietario = datoAEditar.nitPropietario
              this.form.cuiPropietario = datoAEditar.cuiPropietario
              this.form.nombrePropietario = datoAEditar.nombrePropietario
              this.form.tipo = datoAEditar.tipo
              this.form.marca = datoAEditar.marca
              this.form.linea = datoAEditar.linea
              this.form.modelo = datoAEditar.modelo
              this.form.placa = datoAEditar.placa
              this.form.vin = datoAEditar.vin
              this.form.chasis = datoAEditar.chasis
              this.form.color = datoAEditar.color
            }
            this.$refs['modal-2'].show()
            break
          }
          case 'delete': {
            const datoAEliminar = this.datosPosts.find(dato => dato.id === id)
            if (datoAEliminar) {
              this.form.id = datoAEliminar.id
              this.form.nombrePropietario = datoAEliminar.nombrePropietario
              this.form.marca = datoAEliminar.marca
              this.form.linea = datoAEliminar.linea
              this.form.modelo = datoAEliminar.modelo
              this.form.placa = datoAEliminar.placa
              console.log(this.form.id)
              console.log(this.form.nombre)
            }
            this.$refs['modal-3'].show()
            break
          }
        }
      },
      closeModal (action) {
        switch (action) {
          case 'save': {
            this.$v.$reset()
            this.$refs['modal-1'].hide()
            this.form.id = 0
            this.form.nitPropietario = ''
            this.form.cuiPropietario = ''
            this.form.nombrePropietario = ''
            this.form.tipo = ''
            this.form.marca = ''
            this.form.linea = ''
            this.form.modelo = ''
            this.form.placa = ''
            this.form.vin = ''
            this.form.chasis = ''
            this.form.color = ''
            break
          }
          case 'update': {
            this.$v.$reset()
            this.$refs['modal-2'].hide()
            this.form.id = 0
            this.form.nitPropietario = ''
            this.form.cuiPropietario = ''
            this.form.nombrePropietario = ''
            this.form.tipo = ''
            this.form.marca = ''
            this.form.linea = ''
            this.form.modelo = ''
            this.form.placa = ''
            this.form.vin = ''
            this.form.chasis = ''
            this.form.color = ''
            break
          }
        }
      },
      onValidate (action) {
        this.$v.$touch()
        if (this.$v.$error !== true) {
          if (action === 'save') {
            this.onSave()
          } else if (action === 'update') {
            this.onState()
          }
        }
      },
      setData (data) {
        this.form.user = data.user
        this.form.state = data.estado
        this.form.id = data.id
      },
      /* Guardar */
      onSave () {
        const me = this
        axios.post(laravelUrl + '/api/vehiculo/create/', {
          nitPropietario: me.form.nitPropietario,
          cuiPropietario: me.form.cuiPropietario,
          nombrePropietario: me.form.nombrePropietario,
          tipo: me.form.tipo,
          marca: me.form.marca,
          linea: me.form.linea,
          modelo: me.form.modelo,
          placa: me.form.placa,
          vin: me.form.vin,
          chasis: me.form.chasis,
          color: me.form.color,
          estadoActivo: 1
          })
          .then((response) => {
            me.getDatos()
            me.closeModal('save')
          })
          .catch((error) => {
            // this.errorMessage = error.message;
            console.error('Error!', error)
          })
      },
      /* Guardar */
      onUpdate () {
        const me = this
        axios.put(apiUrl + '/user/update', {
          form: me.form })
          .then((response) => {
            me.closeModal('update')
          })
          .catch((error) => {
            // this.errorMessage = error.message;
            console.error('Error!', error)
          })
      },
      onState () {
        const me = this
        axios.put(laravelUrl + '/api/vehiculo/update/' + this.form.id, {
          nitPropietario: me.form.nitPropietario,
          cuiPropietario: me.form.cuiPropietario,
          nombrePropietario: me.form.nombrePropietario,
          tipo: me.form.tipo,
          marca: me.form.marca,
          linea: me.form.linea,
          modelo: me.form.modelo,
          placa: me.form.placa,
          vin: me.form.vin,
          chasis: me.form.chasis,
          color: me.form.color,
          estadoActivo: 1  })
          .then((response) => {
            me.getDatos()
            me.closeModal('update')
          })
          .catch((error) => {
            // this.errorMessage = error.message;
            console.error('Error!', error)
          })
      },
      DeleteData () {
        const me = this
        axios.delete(laravelUrl + '/api/vehiculo/delete/' + this.form.id, {
        })
          .then((response) => {
            me.getDatos()
            me.closeModal('update')
          })
          .catch((error) => {
          // this.errorMessage = error.message;
            console.error('Error!', error)
          })
      },
      makeQueryParams (sortOrder, currentPage, perPage) {
        return sortOrder[0]
          ? {
            criterio: sortOrder[0] ? sortOrder[0].sortField : 'createdAt',
            order: sortOrder[0] ? sortOrder[0].direction : 'desc',
            page: currentPage,
            limit: this.perPage,
            search: this.search,
            columna: this.columna.value
          }
          : {
            criterio: sortOrder[0] ? sortOrder[0].sortField : 'createdAt',
            order: sortOrder[0] ? sortOrder[0].direction : 'desc',
            page: currentPage,
            limit: this.perPage,
            search: this.search,
            columna: this.columna.value
          }
      },
      changePageSizes (perPage) {
        this.perPage = perPage
        this.$refs.vuetable.refresh()
      },
      searchChange (val) {
        this.search = val.toLowerCase()
        this.$refs.vuetable.refresh()
      },
      onPaginationData (paginationData) {
        this.from = paginationData.from
        this.to = paginationData.to
        this.total = paginationData.total
        this.lastPage = paginationData.last_page
        this.items = paginationData.data
        this.$refs.pagination.setPaginationData(paginationData)
      },
      onChangePage (page) {
        this.$refs.vuetable.changePage(page)
      },
      changeTypeSearch (columna) {
        this.columna = columna
      },
      mensaje (mensaje) {
        this.form.mensaje = mensaje
      },
      mensajeDespedida () {
        console.log('Antes de irnos del componente manda este mensaje')
      }
    }
  }
  </script>
  