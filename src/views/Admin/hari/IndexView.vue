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
          <button class="mr-4 hover:underline md:mr-6">Data Hari</button>
        </li>
      </ul>
      <br />
    </div>

    <b>Data Semua Hari</b>


    <div class="relative overflow-x-auto shadow-md sm:rounded-lg">
    <table class="w-full text-sm text-left text-gray-500 dark:text-gray-400">
        <thead class="text-xs text-gray-700 uppercase bg-gray-50 dark:bg-gray-700 dark:text-gray-400">
            <tr>
                <th scope="col" class="px-6 py-3">
                   NO
                </th>
                <th scope="col" class="px-6 py-3">
                   HARI
                </th>
            </tr>
        </thead>
        <tbody>
            <tr v-for="(item, index) in hari" :key="item.id" class="bg-white border-b dark:bg-gray-800 dark:border-gray-700 hover:bg-gray-50 dark:hover:bg-gray-600">
                <th scope="row" class="flex items-center px-6 py-4 text-gray-900 whitespace-nowrap dark:text-white">
                  {{ index + 1 }}
                </th>
                <td class="px-6 py-4">
                  {{ item.hari }}
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
    ...mapState("hari", ["hari"]),
  },
  mounted() {
    this.$store.dispatch("hari/fecthari");
  },
  setup(props, context) {
    onMounted(() => {
      try {
        context.emit("id-menu", 5);
      } catch (error) {
        console.log(error);
      }
    });
  },
};
</script>
