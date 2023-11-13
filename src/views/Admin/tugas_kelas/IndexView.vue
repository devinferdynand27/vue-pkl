<template>
  <div class="p-4 sm:ml-64">
    <br /><br /><br />
    <div class="list">
      <ul class="flex flex-wrap items-center text-gray-900 dark:text-white">
        <li style="color: black">
          <a href="#" class="mr-4 hover:underline md:mr-6">
            <i style="font-size: 20px" class="bi bi-house-door-fill"></i>
          </a>
        </li>
        <li style="color: black">
          <a href="#" class="mr-4 hover:underline md:mr-6"
            ><i class="bi bi-arrow-right"></i
          ></a>
        </li>
        <li style="color: black">
          <button class="mr-4 hover:underline md:mr-6">Data Kelas</button>
        </li>
      </ul>
      <br />
    </div>

    <b>Data Semua Tugas Harian</b>

    &nbsp;
    <div class="relative mt-6 overflow-x-auto shadow-md sm:rounded-lg">
      <table class="w-full text-sm text-left">
        <thead
          class="text-xs text-white uppercase bg-blue-600 border-b border-blue-400 dark:text-white"
        >
          <tr>
            <th scope="col" class="px-6 py-3" style="color: black">
              Mata Pelajaran
            </th>
            <th scope="col" class="px-6 py-3" style="color: black">Kelas</th>
            <th scope="col" class="px-6 py-3" style="color: black">Hari</th>
            <th scope="col" class="px-6 py-3" style="color: black">Action</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="item in tugas" :key="item.id">
            <td
              v-if="item.id_kelas == id"
              class="px-6 py-4"
              style="color: black"
            >
              {{ item.mapel }}
            </td>
            <td
              v-if="item.id_kelas == id"
              class="px-6 py-4"
              style="color: black"
            >
              {{ item.kelas }}
            </td>
            <td
              v-if="item.id_kelas == id"
              class="px-6 py-4"
              style="color: black"
            >
              {{ item.hari }}
            </td>
            <!-- <td class="px-6 py-4" style="color: black">
              {{ item.tugas }}
            </td> -->
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>
<script>
import axios from "axios";
import { ref } from "vue";
import { onMounted } from "vue";
import { mapActions, mapState } from "vuex";
export default {
  props: ["id"],
  computed: {
    ...mapState("tugas", ["tugas"]),
  },
  mounted() {
    this.$store.dispatch("tugas/fecttugas");
  },

  setup(props, context) {
    onMounted(() => {
      try {
        context.emit("id-menu", 8);
      } catch (error) {
        console.log(error);
      }
    });
  },
};
</script>
