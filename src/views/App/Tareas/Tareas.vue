<template>
    <b-container fluid>
      <b-modal id="modal-1" ref="modal-1" size="xl" title="Nueva Tarea">
        <form>
          <div class="col-md-12 mb-3">
            <label for="nombre">Nombre</label>
            <input
              required
              type="text"
              class="form-control"
              id="nombre"
              v-model.trim="$v.form.nombre.$model"
              :state="!$v.form.nombre.$error"
              placeholder="Ingresar nombre"
          >
          </div>
          <div class="col-md-12 mb-3">
            <label for="descripcion">Descripcion</label>
            <input
              required
              class="form-control"
              id="descripcion"
              v-model.trim="$v.form.descripcion.$model"
              :state="!$v.form.descripcion.$error"
              placeholder="Ingresar descripcion"
            >
          </div>
        </form>
        <template #modal-footer="{}">
          <b-button  variant="primary" @click="onSave()"
            >Guardar</b-button
          >
          <b-button variant="danger" @click="closeModal('save')"
            >Cancelar</b-button
          >
        </template>
      </b-modal>
      <b-modal id="modal-2" ref="modal-2" title="Editar Alumno">
        <form>
          <div class="col-md-12 mb-3">
            <label for="user">Nombre</label>
            <input
              required
              type="text"
              class="form-control"
              id="nombre"
              v-model.trim="$v.form.nombre.$model"
              :state="!$v.form.nombre.$error"
            >
          </div>
          <div class="col-md-12 mb-3">
            <label for="descripcion">Descripcion</label>
            <input
              required
              type="text"
              class="form-control"
              id="descripcion"
              v-model.trim="$v.form.descripcion.$model"
              :state="!$v.form.descripcion.$error"
            >
          </div>
        </form>
        <template #modal-footer="{}">
          <b-button  variant="primary" @click="onState()"
            >Editar</b-button
          >
          <b-button variant="danger" @click="closeModal('update')"
            >Cancelar</b-button
          >
        </template>
      </b-modal>
      <b-modal id="modal-3" ref="modal-3" title="Eliminar Alumno">
        <h6 class="my-4">
          ¿Desea eliminar la Tarea: {{ form.nombre }} ?
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
                <h4 class="card-title mt-3">TAREAS</h4>
              </template>
              <template v-slot:headerAction>
                <b-button variant="primary" @click="$refs['modal-1'].show()">AGREGAR NUEVO</b-button>
            </template>
            <template v-slot:body>
              <table class="table table-striped custom-table mb-0">
                  <thead>
                    <th>
                        Id Tarea
                    </th>
                      <th>
                          Nombre
                      </th>
                      <th>
                          Descripcion
                      </th>
                      <th>
                          Estado
                      </th>
                      <th>
                          Acciones
                      </th>
                  </thead>
                  <tbody>
                      <tr v-for="datos in datosPosts" :key="datos.id">
                            <td v-text="datos.id"></td>
                          <td v-text="datos.nombre"></td>
                          <td v-text="datos.descripcion"></td>
                          <td v-if="datos.state === 1">Pendiente</td>
                          <td v-if="datos.state === 0">Entregado</td>
                          <td v-if="datos.state === 3">Cancelada</td>
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
  name: 'Alumnos',
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
          nombre: '',
          descripcion: '',
          state: ''
        },
        apiBase: laravelUrl + '/api/tarea/get',
      }
    },
    validations () {
      return {
        form: {
          nombre: { required },
          descripcion: { required },
        }
      }
    },
    methods: {
      getDatos () {
        axios.get(laravelUrl + '/api/tarea/get').then((response) => {
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
            this.form.nombre = ''
            this.form.descripcion = ''
            break
          }
          case 'update': {
            const datoAEditar = this.datosPosts.find(dato => dato.id === id)
            if (datoAEditar) {
              this.form.id = datoAEditar.id
              this.form.nombre = datoAEditar.nombre
              this.form.descripcion = datoAEditar.descripcion
            }
            this.$refs['modal-2'].show()
            break
          }
          case 'delete': {
            const datoAEliminar = this.datosPosts.find(dato => dato.id === id)
            if (datoAEliminar) {
              this.form.id = datoAEliminar.id
              this.form.nombre = datoAEliminar.nombre
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
            this.form.nombre = ''
            this.form.descripcion = ''
            break
          }
          case 'update': {
            this.$v.$reset()
            this.$refs['modal-2'].hide()
            this.form.id = 0
            this.form.nombre = ''
            this.form.descripcion = ''
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
        axios.post(laravelUrl + '/api/tarea/create', {
          nombre: me.form.nombre,
          descrpcion: me.form.descrpcion})
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
        axios.put(laravelUrl + '/api/tarea/update/' + this.form.id, {
          nombre: me.form.nombre,
          descripcion: me.form.descripcion })
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
        axios.delete(laravelUrl + '/api/tarea/delete/' + this.form.id, {
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
  