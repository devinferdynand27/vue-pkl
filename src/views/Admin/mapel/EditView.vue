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
            Tambah Mata-Pelajaran
          </button>
        </li>
      </ul>
    </div>
    <br />
    <div class="card shadow-md pl-4 pr-4">
      <br />
      <form @submit.prevent="editmapels" class="pl-4 pr-4" method="post">
        <div>
          <label
            for="mapel"
            style="color: black"
            class="float-left block mb-2 text-sm font-medium text-gray-900 dark:text-white"
            >Masukan Mata-Pelajaran</label
          >
          <input
            type="text"
            v-model="editmapel.mapel"
            class="mb-3 bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-600 dark:border-gray-500 dark:placeholder-gray-400 dark:text-white"
          /><br />
        </div>

        <button
          class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded"
        >
          Simpan
        </button>
        <br /><br />
      </form>
    </div>
  </div>
</template>

<script>
import { onMounted } from "vue";
import { mapActions, mapState } from "vuex";
export default {
  props: ["id"],
  data() {
    return {
      editmapel: {
        mapel: null,
      },
    };
  },
  computed: {
    ...mapState("mapel", ["singlemapel"]),
  },
  mounted() {
    this.$store.dispatch("mapel/fectmapelshow", this.id);
    this.editmapel.mapel = this.singlemapel.mapel;
  },
  methods: {
    ...mapActions("mapel", ["fetchmapeledit"]),
    editmapels() {
      this.fetchmapeledit(this.editmapel);
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
