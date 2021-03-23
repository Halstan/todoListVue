<template>
  <table class="table table-dark">
    <thead>
      <tr>
        <th scope="col">#</th>
        <th scope="col">Nombre</th>
        <th scope="col">Categorias</th>
        <th scope="col">Importancia</th>
        <th scope="col">Hora</th>
        <th scope="col">Finalizado</th>
        <th scope="col">Accion</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="tarea in tareas" :key="tarea.id">
        <th>{{ tarea.id }}</th>
        <td>{{ tarea.nombre }}</td>
        <td>
          <span v-for="(categoria, index) in tarea.categorias" :key="index">
            {{
              tarea.categorias.length === index + 1
                ? categoria
                : categoria + ", "
            }}
          </span>
        </td>
        <td>{{ tarea.importancia }}</td>
        <td>{{ tarea.hora }}</td>
        <td>{{ tarea.isFinish ? "Terminado" : "Incompleto" }}</td>
        <td>
          <button class="btn btn-danger" @click="deleteTarea(tarea.id)">
            Eliminar
          </button>
          <router-link
            class="btn btn-primary ml-2"
            :to="{ name: 'Editar', params: { id: tarea.id } }"
            >Editar</router-link
          >
        </td>
      </tr>
    </tbody>
  </table>
</template>

<script>
import { mapState, mapActions } from "vuex";

export default {
  name: "ListaTareas",
  computed: {
    ...mapState(["tareas"]),
  },
  methods: {
    ...mapActions(["deleteTarea"]),
  },
};
</script>

<style></style>
