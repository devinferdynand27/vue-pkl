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
          <button class="mr-4 hover:underline md:mr-6">
            Data Mata-Pelajaran
          </button>
        </li>
      </ul>
      <br />
    </div>

    <b>Data Semua Mata-Pelajaran</b>

    <router-link to="/admin/mata-pelajaran/create">
      <a
        class="float-right cursor-pointer bg-green-500 hover:bg-green-700 text-white font-bold py-2 px-4 rounded btn-sm"
        >Tambah Mata-Pelajaran</a
      >
    </router-link>

    &nbsp;
    <br><br>
    <div class="relative overflow-x-auto shadow-md sm:rounded-lg">
    <table class="w-full text-sm text-left text-gray-500 dark:text-gray-400">
        <thead class="text-xs text-gray-700 uppercase bg-gray-50 dark:bg-gray-700 dark:text-gray-400">
            <tr>
                <th scope="col" class="px-6 py-3">
                   NO
                </th>
                <th scope="col" class="px-6 py-3">
                   Mata - Pelajaran
                </th>
                <th scope="col" class="px-6 py-3">
                   Action
                </th>
            </tr>
        </thead>
        <tbody>
            <tr v-for="(item, index) in mapel" :key="item.id" class="bg-white border-b dark:bg-gray-800 dark:border-gray-700 hover:bg-gray-50 dark:hover:bg-gray-600">
                <th scope="row" class="flex items-center px-6 py-4 text-gray-900 whitespace-nowrap dark:text-white">
                  {{ index + 1 }}
                </th>
                <td class="px-6 py-4">
                  {{ item.mapel }}
                </td>
                <td>
              <router-link :to="'/admin/mata-pelajaran/edit/' + item.id">
                <a
                  href="#"
                  class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded btn-sm"
                  ><i class="bi bi-pen-fill"></i
                ></a>
                &nbsp;
              </router-link>
              <a
                href="#"
                @click="deletes(item.id)"
                class="bg-red-500 hover:bg-red-700 text-white font-bold py-2 px-4 rounded btn-sm"
                ><i class="bi bi-trash2"></i
              ></a>
            </td>
            </tr>
        </tbody>
    </table>
</div>
  </div>
</template>
<script>
import { onMounted } from "vue";
import { mapActions, mapState } from "vuex";
export default {
  computed: {
    ...mapState("mapel", ["mapel"]),
  },
  mounted() {
    this.$store.dispatch("mapel/fectmapel");
  },
  methods: {
    ...mapActions("mapel", ["fectmapeldelete"]),
    deletes(params) {
      this.fectmapeldelete(params);
    },
  },
  setup(props, context) {
    onMounted(() => {
      try {
        context.emit("id-menu", 6);
      } catch (error) {
        console.log(error);
      }
    });
  },
};
</script>
