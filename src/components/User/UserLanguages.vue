<template>
  <v-card>
    <v-card-title class="card-title">Languages</v-card-title>
    <v-simple-table>
      <template v-slot:default>
        <thead>
        <tr>
          <th class="text-left">Language</th>
          <th class="text-left">Proficiency</th>
        </tr>
        </thead>
        <tbody>
        <tr v-for="(l, idx) in user.languages" :key="idx">
          <td>{{ l.language }}</td>
          <td>{{ l.proficiency }}</td>
        </tr>
        </tbody>
      </template>
    </v-simple-table>
  </v-card>
</template>

<script>
  export default {
    name: "UserLanguages",
    props: ["user"],
  }
</script>

<style scoped>
.card-title {
  color: white;
  background-color: #dd2c00;
}
</style>
