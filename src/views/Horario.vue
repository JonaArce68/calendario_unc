<template>
  <div class="body-horarios">
    <div class="container col-xxl-12">
      <div class="container-1-linea col-2">
        <div class="container-h2 mt-4 col-12">
          <h3 class="h2">Nuevo Horario:</h3>
        </div>

        <div class="container-input mt-2 col-12">
          <input
            type="text"
            class="col-9 bg-light rounded"
            v-model="nuevoHorario"
            v-on:keyup.enter="agregarHorario"
            placeholder="  Agrega un Horario"
          />

          <b-button
            id="basic-addon"
            class="input-group-text col-3 bi bi-plus-circle-fill"
            variant="outline"
            @click="agregarHorario"
          >
          </b-button>
        </div>

        <b-dropdown
          id="lista-horarios"
          name="Listado De Horarios"
          text="Tus Horarios"
          class="my-4 col-12 boton-titulos"
        >
          <b-dropdown-item
            v-for="item of horarios"
            :key="item.id"
            @click="mostrarHorario(item)"
          >
            <div class="d-flex justify-content-between">
              <div>{{ item.id }} - {{ item.nombre }}</div>

              <div>
                <b-button
                  variant="danger"
                  class="btn-sm"
                  @click="eliminarHorario"
                  >X</b-button
                >
                <b-button class="bi bi-pencil btn-sm" variant="info"></b-button>
              </div>
            </div>
          </b-dropdown-item>
        </b-dropdown>
        <!-- Nombre Tabla -->

        <p class="h3 text-capitalize">{{ selectedHorario.nombre }}</p>

        <hr />

        <div class="containerbotones col-12">
          <p class="h5">
            Personalizá tus actividades y materias según tus tiempos.
          </p>

          <div class="containeract my-3">
            <!-- creador de actividad -->
            <button
              v-b-modal.modal-Actividad
              variant="outline-info"
              class="boton-horario col-12 mb-2"
            >
              Nueva Actividad
            </button>

            <b-modal id="modal-Actividad" centered title="Actividad">
              <p class="my-4">Agregue una actividad</p>

              <div class="input-group mb-3" bg-secondary>
                <div class="input-group-prepend">
                  <input
                    type="text"
                    class="form-control"
                    v-model="nuevaActividad"
                    v-on:keyup.enter="agregarActividad"
                  />
                  Desde
                  <input type="time" class="form-control" />

                  Hasta
                  <input type="time" class="form-control" />
                  <b-button
                    id="basic-addon"
                    class="input-group-text bi bi-plus-circle-fill"
                    variant="outline"
                    @click="agregarActividad"
                  >
                  </b-button>
                </div>

                <b-list class="">
                  <b-item v-for="item of actividades" :key="item.nombre">
                    <div class="d-flex justify-content-between">
                      <div>{{ index }} - {{ item.nombre }}</div>

                      <div>
                        <b-button
                          variant="danger"
                          class="btn-sm"
                          @click="eliminarActividad"
                          >X</b-button
                        >
                      </div>
                    </div>
                  </b-item>
                </b-list>
              </div>
            </b-modal>
          </div>
          <!-- cierre container act -->
          <div class="containermateria mb-4">
            <button
              v-b-modal.modal-materia
              variant="outline-warning"
              class="boton-horario col-12"
            >
              Nueva Materia
            </button>
            <!-- acá va el modal de materias -->
            <b-modal
              id="modal-materia"
              size="lg"
              centered
              title="Seleccione una carrera"
            >
              <!-- Selección de Carreras -->
<<<<<<< HEAD
              <b-row class="d-flex flex-column">
                <b-col class="d-flex" cols="12">
                  <p class="h6">Facultad</p>
                  <b-form-select
                    :value="seleccionFacu"
                    :options="optionsFacu"
                    @change="changeSelectedFacultad"
                    size="sm"
                    class="mt-3 drowdown-items"
                   
                  >
                  </b-form-select>
                </b-col>

                <div class="d-flex flex-column">
                  <hr width="100%" style="color: #ddc77a" />
                  <b-col class="d-flex">
                    <p class="h6">Carrera</p>
                    <b-form-select
                      :value="seleccionCareer"
                      :options="optionsCareer"
                      @change="changeSelectedCareer"
                      size="sm"
                      class="mt-3 drowdown-items"
                     
                    >
                    </b-form-select>
                  </b-col>

                  <hr width="100%" style="color: #ddc77a" />
                  <b-col class="d-flex" cols="12">
                    <!-- Listado de Carreras -->
                    <b-col class="d-flex">
                      <p class="h6">Semestre</p>
                      <b-form-select
                        :value="seleccionSem"
                        :options="optionsPeriodos"
                        @change="changeSelectedPeriodo"
                        size="sm"
                        class="mt-3 drowdown-items"
                      >
                      </b-form-select>
                    </b-col>
                    <b-col class="d-flex">
                      <p class="h6">Año de Carrera</p>
                      <b-form-select
                        :value="seleccionAnios"
                        :options="optionsAnios"
                        @change="changeSelectedAnio"
                        size="sm"
                        class="mt-3 drowdown-items"
                      >
                      </b-form-select>
                    </b-col>
                  </b-col>
                  <hr width="100%" style="color: #ddc77a" />
                </div>
              </b-row>
=======
            <b-row class="d-flex flex-column" cols-md="3">
              <p class="h6">Facultad</p>
              <b-form-select
                  :value="seleccionFacu"
                  :options="optionsFacu"
                  @change="changeSelectedFacultad"
                  size="sm"
                  class="mt-3 text-center"
                  style="background-color: beige"
                >
                </b-form-select>
            
              <div class="d-flex flex-column">
                <b-col cols="8">
                <p class="h6">Carrera</p>
                <b-form-select
                  :value="seleccionCareer"
                  :options="optionsCareer"
                  @change="changeSelectedCareer"
                  size="m"
                  class="mt-3"
                  id="selectCarrera"
                  style="background-color: beige"
                >
                </b-form-select>
                
                <b-form-select
                :value="seleccionSem"
                  :options="optionsPeriodos"
                  @change="changeSelectedPeriodo"
                  size="sm"
                  class="mt-3"
                  id="selectPeriodo"
                  style="background-color: beige"
                >
                </b-form-select>
                <b-form-select
                :value ="seleccionAnio"
                  :options="optionsAnios"
                  @change="changeSelectedAnio"
                  size="sm"
                  class="mt-3"
                  id="selectAnio"
                  style="background-color: beige"
                >
                </b-form-select>
              </b-col>
                <!-- <div class="mt-3 mx-5">
                  Código de Carrera:
                  <strong class="mx-3">{{ seleccion }}</strong>
                </div> -->
              </div>
            </b-row>
>>>>>>> 3c1cd8ac9045032be88c4bbf0fc13c2383c2b6df
              <!-- cierre Selección de Carreras -->
              <b-row>
                <div class="">
                  <p class="mt-3">Listado de materias</p>
                  <div class="">
                    <b-table
                      striped
                      hover
                      :items="listadoMaterias"
                      @row-clicked="materiaRowClicked"
                    >
                      <template slot="row-details">
<<<<<<< HEAD
                        <b-list-group v-for="com in comisionList" :key="com">
                          <b-list-group-item>{{ com }}</b-list-group-item>
                        </b-list-group>
                        <b-form-group>
                          <template #label>
                            <b-form-checkbox
                              v-model="allSelected"
                              :indeterminate="indeterminate"
                              aria-describedby="comisionList"
                              aria-controls="comisionList"
                              @change="toggleAll"
                            >
                              {{
                                allSelected
                                  ? "Quitar seleccion"
                                  : "Seleccionar todo"
                              }}
                            </b-form-checkbox>
                          </template>

                          <template v-slot="{ ariaDescribedby }">
                            <b-form-checkbox-group
                              id="comisiones"
                              v-model="selected"
                              :options="comisionList"
                              :aria-describedby="ariaDescribedby"
                              name="comisiones"
                              class="ml-4 mx-2"
                              aria-label="Listado De Comisiones"
                              stacked
                            ></b-form-checkbox-group>
                          </template>
                        </b-form-group>
=======
                        <!-- <b-list-group v-for="com in comisionList" :key="com">
                          <b-list-group-item>{{ com }}</b-list-group-item> -->
                          <b-form-group>
                            <template #label>
                              <b-form-checkbox
                                v-model="allSelected"
                                :indeterminate="indeterminate"
                                aria-describedby="comisionList"
                                aria-controls="comisionList"
                                @change="toggleAll"
                              >
                                {{
                                  allSelected
                                    ? "Quitar seleccion"
                                    : "Seleccionar todo"
                                }}
                              </b-form-checkbox>
                            </template>
                      
                            <template v-slot="{ ariaDescribedby }">
                              <b-form-checkbox-group
                                id="comisiones"
                                v-model="selected"
                                :options="comisionList"
                                :aria-describedby="ariaDescribedby"
                                name="comisiones"
                                class="ml-4 mx-2"
                                aria-label="Listado De Comisiones"
                                stacked
                              ></b-form-checkbox-group>
                            </template>
                          </b-form-group>
>>>>>>> 3c1cd8ac9045032be88c4bbf0fc13c2383c2b6df
                        <!-- </b-list-group> -->
                      </template>
                    </b-table>
                  </div>
                </div>
              </b-row>
            </b-modal>
          </div>
          <!--cierre container materias--  -->
        </div>
      </div>

      <!-- cierre div container linea 1 -->

      <b-col class="p-2 bg-light">
        <p class="h2 text-capitalize text-center">
          {{ selectedHorario.nombre }}
        </p>
        <b-row class="border border-dark rounded justify-content-center">
          <b-row
            class="bg-light d-flex-row justify-content-center p-1 m-2 w-100"
          >
            <div>
              <b-table hover :items="dias"></b-table>
              <!-- <div>Selected: <strong>{{ selected }}</strong></div> -->
            </div>
          </b-row>

          <b-row>
            <blockquote class="blockquote text-end">
              <button class="boton-modal pdf col-4">PDF</button>
              <button class="boton-modal excel col-4 ms-4">EXCEL</button>
            </blockquote>
          </b-row>
        </b-row>
      </b-col>
    </div>

    <img
      alt="logo-UNC"
      id="unc1"
      src="@/assets/UNC2.svg"
      class="img-fluid col-5"
    />
  </div>
</template>

<script>
import * as horarios from "@/api/horarios";
import { http } from "../utils/axios";

export default {
  data() {
    return {
      nuevoHorario: "",
      horarios: [],
      facultadesList: {},
      careerList: {}, //variable auxiliar
      nuevaActividad: "",
      actividades: [],
      name: "",
      selectedHorario: {},
      selectedMateriasArray: [],
      selectedMateria: null,
      seleccionSem: null,
      seleccionFacu: null,
<<<<<<< HEAD
      seleccionAnios: null,
      seleccionCareer: null,
      selected: [],
      seleccion: null,
      optionsCareer: [{ value: "null", text: "Seleccione su Carrera" }], //materias
      optionsFacu: [{ value: "null", text: "Seleccione su Facultad" }], //facultades
      optionsPeriodos: [{ value: "null", text: "Seleccione un Semestre" }], //semestres
      listadoMaterias: [],
=======
      seleccionCareer: null,
      seleccionPeriodo: null,
      seleccionAnio: null,
      selected: [],
      seleccion: null,
      optionsCareer: [{ value: "null", text: "Seleccione su Carrera" }],//materias
      optionsFacu: [{ value: "null", text: "Seleccione su Facultad" }],//facultades
      optionsPeriodos: [{ value: "null", text: "Seleccione un Semestre" }],//semestres
      listadoMaterias: [], 
>>>>>>> 3c1cd8ac9045032be88c4bbf0fc13c2383c2b6df
      nameComision: [],
      detailsComision: {},
      comisionList: [],
      allSelected: false,
      indeterminate: false,
      itemsCarrer: [],
      itemsFacultades: [],
<<<<<<< HEAD
      itemsFacultades: [],
      id: [],
      periodosList: {},
      periodos: {},
      optionsAnios: [
        { value: "null", text: "Seleccione un Año" },
        { value: "1", text: "1ro" },
        { value: "2", text: "2ro" },
        { value: "3", text: "3ro" },
        { value: "4", text: "4ro" },
        { value: "5", text: "5ro" },
        { value: "6", text: "6ro" },
      ],
=======
      id:[],
      periodosList:{},
      periodos:{},  
      optionsAnios: [{ value: "1", text: "1ro" },
                    { value: "2", text: "2ro" },
                    { value: "3", text: "3ro" },
                    { value: "4", text: "4ro" },
                    { value: "5", text: "5ro" },
                    { value: "6", text: "6ro" }],
>>>>>>> 3c1cd8ac9045032be88c4bbf0fc13c2383c2b6df
    };
  },
  computed: {
    dias() {
      return [
        {
          hora: "8:00",
          lunes: "FISICA 1-Aula 203",
          martes: "",
          miercoles: "AMI-Aula 205",
          jueves: "",
          viernes: "",
          sabado: "",
        },
        {
          hora: "9:00",
          lunes: "FISICA 1-Aula 203",
          martes: "",
          miercoles: "AMI-Aula 205",
          jueves: "",
          viernes: "AMI-Aula 205",
          sabado: "",
        },
        {
          hora: "10:00",
          lunes: "ALGEBRA-Aula 504",
          martes: "REP ASISTIDA-Aula 500",
          miercoles: "AMI-Aula 205",
          jueves: "",
          viernes: "AMI-Aula 205",
          sabado: "",
        },
        {
          hora: "11:00",
          lunes: "ALGEBRA-Aula 504",
          martes: "REP ASISTIDA-Aula 500",
          miercoles: "",
          jueves: "QUIMICA-Aula 228",
          viernes: "AMI-Aula 205",
          sabado: "",
        },
        {
          hora: "12:00",
          lunes: "ALGEBRA-Aula 504",
          martes: "REP ASISTIDA-Aula 500",
          miercoles: "",
          jueves: "QUIMICA-Aula 228",
          viernes: "AMI-Aula 205",
          sabado: "",
        },
      ];
    },
  },

  async created() {
    try {
      // para los horarios
      const horarios = await this.getHorarios();
      this.selectedHorario = horarios[0];
      this.selectedMateriasArray = Object.keys(this.selectedHorario.materias);
      this.selectedMateria =
        this.selectedHorario.materias[this.selectedMateriasArray[0]];
      // Cierre funcion horarios
      const facultadesList = await this.getFacultadesList();
      this.facultadesList = facultadesList;
      console.log(facultadesList.data);
      //this.optionsFacu = Object.keys(this.facultadesList).map((key) => {
      //  return { value: key, text: this.facultadesList[key] };
      //});
      // const careerList = await this.getCareerList();
      // this.careerList = careerList.data.carreras;
    } catch (error) {
      console.log(error);
    }
  },

  methods: {
    toggleAll(checked) {
      this.selected = checked ? this.comisionList.slice() : [];
    },

    allSelectedOptionsReadyToListMaterias: function() {
      var selectCarrera = document.getElementById("selectCarrera");
      var selectPeriodo = document.getElementById("selectPeriodo");
      var selectAnio = document.getElementById("selectAnio");
      
      if(selectCarrera.options[selectCarrera.selectedIndex] == undefined ||
        selectPeriodo.options[selectPeriodo.selectedIndex] == undefined ||
        selectAnio.options[selectAnio.selectedIndex] == undefined){
        return false;
      }else{
        return true;
      }
    },

    fillMateriasYComisionesList: async function() {
      this.materiaList = await this.getMateriasList();

    /*
      {
        "FISICA I"{
          "COM1": [],
          "COM2": [],
          "COM3": [],
        },
        "ALGEBRA"{
          "COM1": [],
          "COM2": [],
          "COM3": [],
        },
      }


      listadoMaterias = [FISICA I, ALEGEBRA]


    */
      //Save the keys from this.materiaList.data into this.listadoMaterias

      //this.listadoMaterias = Object.keys(this.materiaList.data);
      this.listadoMaterias = Object.keys(this.materiaList.data).map((key) => {
        return { materia: key }; 
      });


      console.log(this.listadoMaterias);

      // this.listadoMaterias = this.materiaList.data.map((name) => {
      //   return { nombre: name };
      // });

    },



    changeSelectedFacultad: async function (seleccion) {
      this.seleccionFacu = seleccion;
      this.itemsFacultades.seleccionFacu = seleccion;
      await this.getCareerList();
      await this.getPeriodoList();
<<<<<<< HEAD
    },
    changeSelectedCareer: async function (seleccion) {
      this.seleccionCareer = seleccion;
      this.itemsCarrer.selected = seleccion;
      this.materiaList = await this.getMateriasList();
      this.listadoMaterias = this.materiaList.data.nombres.map((name) => {
        return { nombre: name };
      });
=======
      },
    changeSelectedCareer: async function (seleccion) {
      this.seleccionCareer = seleccion;
      this.items.selected = seleccion;
      //this.materiaList = await this.getMateriasList();
      // this.listadoMaterias = this.materiaList.data.nombres.map((name) => {
      //   return { nombre: name };
      // });

      if(this.allSelectedOptionsReadyToListMaterias()){
        console.log("Todos los campos de selection estan listos");

        this.fillMateriasYComisionesList();

      } else{
        console.log("Algun campo de selection no esta listo");
      }

    },

    changeSelectedPeriodo: async function (seleccion) {
      this.seleccionPeriodo = seleccion;
      // this.seleccion = seleccion;
      // this.items.selected = seleccion;
      // this.materiaList = await this.getMateriasList();
      // this.listadoMaterias = this.materiaList.data.nombres.map((name) => {
      //   return { nombre: name };
      // });

      if(this.allSelectedOptionsReadyToListMaterias()){
        console.log("Todos los campos de selection estan listos");

        this.fillMateriasYComisionesList();


      } else{
        console.log("Algun campo de selection no esta listo");
      }

    },

    changeSelectedAnio: async function (seleccion) {
      this.seleccionAnio = seleccion;
      // this.seleccion = seleccion;
      // this.items.selected = seleccion;
      // this.materiaList = await this.getMateriasList();
      // this.listadoMaterias = this.materiaList.data.nombres.map((name) => {
      //   return { nombre: name };
      // });

      if(this.allSelectedOptionsReadyToListMaterias()){

        this.fillMateriasYComisionesList();

        console.log("Todos los campos de selection estan listos");
      } else{
        console.log("Algun campo de selection no esta listo");
      }

>>>>>>> 3c1cd8ac9045032be88c4bbf0fc13c2383c2b6df
    },
    changeSelectedAnio: async function (seleccion) {
      this.seleccionAnios = seleccion;
      this.itemsCarrer.selected = seleccion;
    },
    changeSelectedPeriodo: async function (seleccion) {
      this.seleccionSem = seleccion;
      this.itemsCarrer.selected = seleccion;
    },

    getHorarios: async function () {
      const data = await horarios.get();
      this.horarios = data;
      return data;
    },
    
    getFacultadesList: async function (item) {
      if (this.seleccionFacu == "") return "";
      const dataFacList = await http.get("/facultades");
      this.facultadesList = dataFacList.data;
      console.log(this.facultadesList);

      this.facultadesList = Object.keys(this.facultadesList).map((key) => {
        return { value: key, text: this.facultadesList[key] };
      });

      this.optionsFacu = this.facultadesList;

      return dataFacList;
    },
    getCareerList: async function () {
      if (this.seleccionCareer == "") return "";
      const dataList = await http.get(`/carreras/${this.seleccionFacu}`);
      console.log(dataList);
      this.careerList = dataList.data;
      this.carreras = Object.keys(this.careerList).map((key) => {
        return { value: key, text: this.careerList[key] };
      });
      this.optionsCareer = this.carreras;
      return dataList;
    },

    getPeriodoList: async function () {
      if (this.seleccionSem == "") return "";
      const dataList = await http.get(`/periodo/${this.seleccionFacu}`);
      this.periodosList = dataList.data;
      this.periodos = Object.keys(this.periodosList).map((key) => {
        return { value: key, text: this.periodosList[key] };
      });
      this.optionsPeriodos = this.periodos;
      return dataList;
    },

    getMateriasList: async function () {
<<<<<<< HEAD
      if (!this.seleccionFacu) return [];
      ("/comisiones/{this.seleccionFacu}/{seleccionCareer}/{seleccionSem}/{}");
      const dataMateria = await http.get(
        `/comisiones/${this.seleccionFacu}/${this.seleccionCareer}/${this.seleccionAnios}/${this.seleccionSem}/`
=======
      if (!this.seleccionFacu || !this.seleccionCareer || !this.seleccionPeriodo || !this.seleccionAnio) return [];

      const dataMateria = await http.get(
        `/comisiones/${this.seleccionFacu}/${this.seleccionCareer}/${this.seleccionAnio}/${this.seleccionPeriodo}`
>>>>>>> 3c1cd8ac9045032be88c4bbf0fc13c2383c2b6df
      );
      return dataMateria;
    },
    agregarHorario: async function () {
      await horarios.post({
        nombre: this.nuevoHorario,
        estado: false,
      });
      this.getHorarios();
      this.nuevoHorario = "";
    },
    agregarMateria: function () {
      this.materias.push({
        nombre: this.nuevaMateria,
        estado: false,
      });
      this.nuevaMateria = "";
    },
    agregarActividad: function () {
      this.actividades.push({
        nombre: this.nuevaActividad,
        estado: false,
      });

      this.nuevaActividad = "";
    },
    eliminarHorario: function (index) {
      this.horarios.splice(index, 1);
    },
    eliminarActividad: function (index) {
      this.actividades.splice(index, 1);
    },
    materiaRowClicked: async function (observer) {
      let nombreMateria = observer.materia;

      // 28823957ahjsdhsaj : FISICA 1

      // const comisionResponse = await http.get(
      //   `/get-comisiones/${this.seleccion}/${this.nameComision}`
      // );
      
      let comisiones = this.materiaList.data[nombreMateria];
      console.log(comisiones);


      /*
      Materia 1
            comision 1
            Lunes 8:00-10:00  13:00-16:00  *
            Martes 8:00-10:00

            comision 2
            Lunes 8:00-10:00
            Martes 8:00-10:00

            comision 3
            Lunes 8:00-10:00
            Martes 8:00-10:00
            
      Materia 2
            comision 1 
            Lunes 8:00-10:00    *
            Martes 8:00-10:00

            comision 2
            Lunes 8:00-10:00
            Martes 8:00-10:00

            comision 3
            Lunes 8:00-10:00
            Martes 8:00-10:00
      */
      //nombre materia
      //nombre comision
      //seleccionFacultad
      //seleccionCareer
      //seleccionAnio
      //seleccionPeriodo 
      this.comisionList = Object.keys(comisiones);
      this.$set(observer, "_showDetails", !observer._showDetails);
<<<<<<< HEAD
      let allComisionDetails = Object.entries(comisionResponse.data);
      for (let [key, value] of Object.entries(allComisionDetails)) {
        console.log(`${key}: ${value}`);
        d;
      }
      console.log(allComisionDetails.find((value) => value.value));
=======
      // let allComisionDetails = Object.entries(comisiones);




      // for(let[key, value] of Object.entries(allComisionDetails)){
      //   console.log(`${key}: ${value}`);d
      // }
      // console.log(allComisionDetails.find(value=>value.value))
>>>>>>> 3c1cd8ac9045032be88c4bbf0fc13c2383c2b6df
    },
    facultadRowClicked: async function (observer) {
      this.nameComision = observer.nombre;

      const comisionResponse = await http.get(
        `/get-comisiones/${this.seleccion}/${this.nameComision}`
      );

      this.comisionList = Object.keys(comisionResponse.data)
        .map((key) => key)
        .filter((el) => el !== "Materia");
      this.$set(observer, "_showDetails", !observer._showDetails);
      let allComisionDetails = Object.entries(comisionResponse.data);
      for (let [key, value] of Object.entries(allComisionDetails)) {
        console.log(`${key}: ${value}`);
        d;
      }
      console.log(allComisionDetails.find((value) => value.value));
    },
    datosComisiones: async function (observer) {},
  },
  // seleccionartodo, selecciona todo con un checkbox
  watch: {
    selected(newValue, oldValue) {
      // Handle changes in individual flavour checkboxes
      if (newValue.length === 0) {
        this.indeterminate = false;
        this.allSelected = false;
      } else if (newValue.length === this.comisionList.length) {
        this.indeterminate = false;
        this.allSelected = true;
      } else {
        this.indeterminate = true;
        this.allSelected = false;
      }
    },
  },
};
</script>

<style>
.container {
  position: fixed;
  left: 1%;
  top: 8%;
  background: rgb(245, 245, 245);
  box-shadow: 0px 1px 20px rgb(0 0 0 / 25%);
  border-radius: 10px;
  width: 100vw;
  height: 90vh;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
}

/* volver a colocar width a 20% */
.container-1-linea {
  padding: 0 2%;
  width: 30%;
  position: relative;
  right: 1%;
  border-radius: 10px;
  outline: 1px solid #2c5f66;
  background-color: #2c5f66;
  color: aliceblue;
}

h3 {
  font-size: 1.5em !important;
  font-family: sans-serif;
}
.drowdown-items{
  background-color: #ddc87a62;
                      width: 75%;
                      border-radius: 5px;
                      text-align: center;
                      box-shadow: 0px 0.5px 20px rgb(0 0 0 / 15%);
}
.boton-titulos {
  border: 3px solid #ddc77a;
  border-radius: 5px;
  background-color: #ddc77a;
  color: #2c5f66;
}

.boton-horario {
  height: 2.5em;
  border: none;
  border-radius: 5px;
  background-color: #ddc77a;
  color: #2c5f66;
}

.boton-modal {
  height: 1.5em;
  border: none;
  border-radius: 4px;
  background-color: #ddc77a;
  color: #2c5f66;
}

.input-group {
  display: flex;
  flex-direction: column;
}

.h3-tabla {
  text-align: center;
}

.tabla {
  font-size: 0.95em;
}

.tableModal {
  height: 50vh;
  overflow-y: scroll;
}
</style>
