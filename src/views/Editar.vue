<template>
  <div class="container">
    <h2 class="my-5 text-center">Editar: {{ tarea.nombre }}</h2>
    <form @submit.prevent="updateTarea">
      <Input :tarea="tarea" />
    </form>
  </div>
</template>

<script>
import { mapState, mapActions } from "vuex";
import Input from "../components/Input.vue";

export default {
  components: { Input },
  name: "Editar",
  computed: {
    ...mapState(["tarea"]),
  },
  methods: {
    ...mapActions(["setTarea", "updateTarea"]),
  },
  created() {
    this.setTarea(this.$route.params.id);
  },
};
</script>

<style></style>
