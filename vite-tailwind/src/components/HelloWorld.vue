<script setup>
import { onMounted, ref } from 'vue'
import axios from "axios";

const students = ref([]);

onMounted(async () => { 
  try {
    const response = await axios.get("http://34.82.81.113:3000/students");
    students.value = response.data;
  } catch (error) {
    console.error("Error fetching students:", error);
  }
});
</script>

<template>
 <table class="w-full border-3 text-left bg-slate-300">
  <thead class="border-b">
    <tr>
      <th>Name</th>
      <th>Group</th>
    </tr>
  </thead>
  <tbody class="bg-slate-100">
    <tr class="border-2 px-6" v-for="(stud, index) in students" :key="index">
      <td>{{ stud.name }}</td>
      <td>{{ stud.group }}</td>
    </tr>
  </tbody>
 </table>
</template>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>