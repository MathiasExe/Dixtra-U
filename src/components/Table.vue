<template>
  <v-simple-table height="300px">
    <template v-slot:default>
      <thead>
        <tr>
          <th class="text-left">Tarea</th>
          <th class="text-left">User id</th>
          <th class="text-left">Estado</th>
          <th class="text-left">Acciones</th>
        </tr>
      </thead>
      <tbody :v-if="tasks.lenght > 0 ? true : false">
        
        <tr v-for="task in tasks" :key="task.id">
          <td>{{task.title}}</td>
          <td>{{task.userId}}</td>
          <td>{{task.completed}}</td>
          <td><v-checkbox
            :value=task.completed
    ></v-checkbox></td>
        </tr>
      </tbody>
    </template>
  </v-simple-table>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      tasks: null
    };
  },
  mounted() {
    const comp = this;
    const api = "https://jsonplaceholder.typicode.com/todos";
    axios
      .get(api)
      .then(response => (comp.tasks = response.data))
      .catch(error => console.log(error));
  },
};
</script>