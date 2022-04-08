<template>
  <div class="about">
    <section class="container">
      <h3>ESTUDIANTES REGISTRADOS</h3>
      <table class="table table-success table-striped">
        <thead>
          <tr>
            <td>CODIGO</td>
            <td>NOMBRE</td>
            <td>EDAD</td>
            <td>GENERO</td>
            <td>ESTADO</td>
            <td>OPCIONES</td>
          </tr>
        </thead>
        <tbody>
          <tr v-for="estudiante in estudiantes" :key="estudiante.id">
            <td>{{ estudiante.id }}</td>
            <td>{{ estudiante.nombre }}</td>
            <td>{{ estudiante.edad }}</td>
            <td>{{ estudiante.genero }}</td>
            <td>{{ estudiante.estado }}</td>
            <td>
              <input
                v-on:click="EliminarEstudiantes()"
                type="button"
                value="Eliminar"
                class="btn btn-success"
              />
            </td>
          </tr>
        </tbody>
      </table>
    </section>

    <hr class="container" />
    <!-- Button trigger modal -->
    <form class="container estudiantes">
      <h3>AGREGAR ESTUDIANTES</h3>

      <div class="mb-6 col-md-6 opcion">
        <label for="nombre" class="form-label">Nombre</label>
        <input
          v-model="form.nombre"
          type="text"
          class="form-control"
          id="nombre"
        />
      </div>
      <div class="mb-6 col-md-6 opcion">
        <label for="edad" class="form-label">Edad</label>
        <input v-model="form.edad" type="text" class="form-control" id="edad" />
      </div>
      <div class="mb-6 col-md-6 opcion">
        <label for="genero" class="form-label">Genero</label>
        <input
          v-model="form.genero"
          type="text"
          class="form-control"
          id="genero"
        />
      </div>
      <div class="mb-6 col-md-6 opcion">
        <label for="estado" class="form-label">Estado</label>
        <input
          v-model="form.estado"
          type="text"
          class="form-control"
          id="estado"
        />
      </div>
    </form>
    <input
      v-on:click="AgregaerEstudiantes()"
      type="button"
      value="Registrar"
      class="btn btn-success"
    />
  </div>
</template>
<script>
import axios from "axios";
export default {
  name: "EstudiantesView",

  components: {},

  data() {
    return {
      estudiantes: "",

      form: {
        nombre: "",
        edad: "",
        genero: "",
        estado: "",
      },
    };
  },

  mounted() {
    this.verEstudiantes();
    this.AgregaerEstudiantes;
  },

  methods: {
    verEstudiantes() {
      axios.get("http://localhost:9090/api/students/").then((response) => {
        this.estudiantes = response.data;
        console.log(this.estudiantes);
      });
      /* .catch(error => {
          console.log(error);
        }),  */
    },
    AgregaerEstudiantes() {
      axios
        .post("http://localhost:9090/api/students/", this.form)
        .then((response) => {
          console.log(response);
        });
    },
    EliminarEstudiantes() {
      axios.delete("http://localhost:9090/api/student/:id").then((response) => {
        console.log(response);
      });
      /* axios
    .delete("http://127.0.0.1:8000/api/car/eliminar/" +id_car})
    .catch((error) => {
      console.log(error);
    }); */
    },
  },
};
</script>
<style scoped>
.titulo {
  border: 1px solid red;
  text-align: center;
}
.estudiantes {
  text-align: center;
  width: 50%;
}
.opcion {
  width: 100%;
  text-align: left;
}
</style>