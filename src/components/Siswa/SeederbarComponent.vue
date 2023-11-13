<template>
  <div>
    <button
      v-if="navbarsiswa == true"
      data-drawer-target="logo-sidebar"
      data-drawer-toggle="logo-sidebar"
      aria-controls="logo-sidebar"
      type="button"
      @click="showseed(false)"
      style="background: orange; width: 95%"
      class="inline-flex items-center p-2 mt-2 ml-3 text-sm text-gray-500 rounded-lg sm:hidden hover:bg-gray-100 focus:outline-none focus:ring-2 focus:ring-gray-200 dark:text-gray-400 dark:hover:bg-gray-700 dark:focus:ring-gray-600"
    >
      <span class="sr-only">Open sidebar</span>
      <svg
        class="w-6 h-6"
        aria-hidden="true"
        fill="currentColor"
        viewBox="0 0 20 20"
        xmlns="http://www.w3.org/2000/svg"
      >
        <!-- Bagian SVG Anda -->
      </svg>
      <span class="text-white"> Buka Menu</span>
    </button>

    <aside
      id="logo-sidebar"
      :class="
        navbarsiswa == true
          ? 'fixed top-0 shadow-xl border-0 left-0 z-40 w-64 h-screen transition-transform -translate-x-full sm:translate-x-0'
          : 'fixed top-0 shadow-xl border-0 left-0 z-40 w-64 h-screen transition-transform sm:translate-x-0'
      "
      aria-label="Sidebar"
    >
      <div
        class="h-full px-3 py-4 overflow-y-auto shadow-xl dark:bg-gray-800"
        style="background: orange"
      >
        <div class="grid grid-cols-2 gap-5">
          <span
            v-if="navbarsiswa == false"
            data-drawer-target="logo-sidebar"
            data-drawer-toggle="logo-sidebar"
            aria-controls="logo-sidebar"
            type="button"
            style="cursor: pointer"
            @click="showseed(true)"
            class="inline-flex bg-white p-1 mt-4 mb-4 ml-1 mr-7 rounded sm:hidden focus:outline-none"
          >
            <svg
              class="w-6 h-6"
              aria-hidden="true"
              fill="currentColor"
              viewBox="0 0 20 20"
              xmlns="http://www.w3.org/2000/svg"
            >
              <!-- Bagian SVG Anda -->
            </svg>
            <i class="bi bi-arrow-left-square"></i>
          </span>
          <!-- ... -->
          <div>
            <div class="flex items-center">
              <br /><br /><br />
              <img
                class="w-10 h-10 rounded-full mr-4"
                src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSzaVm_UFZnQazhzrj-BwwjgAPxxdOcEd9lxJHS9dc3U30XQzL_SffjhFsOWt2SycSu4cQ&usqp=CAU"
                alt="Avatar of Jonathan Reinink"
              />
              <div class="text-sm">
                <p class="text-gray-900 leading-none">{{ siswa.name }}</p>
                <p class="text-gray-600">{{ siswa.id_kelas }}</p>
              </div>
            </div>
            <div></div>
          </div>
        </div>
        <hr class="mb-2 mt-2" />

        <ul class="space-y-2 font-medium">
          <!-- Gunakan router-link untuk navigasi -->
          <router-link to="/siswa/dashboard">
            <li :class="setActivedNavClass(rl.dashboard)">
              <a
                class="flex items-center p-2 text-white- rounded-lg dark:text-white group"
              >
                <svg
                  :class="setActivedNavClass(rl.dashboard)"
                  class="w-5 h-5 text-gray-500 transition duration-75"
                  aria-hidden="true"
                  xmlns="http://www.w3.org/2000/svg"
                  fill="currentColor"
                  viewBox="0 0 22 21"
                >
                  <!-- Bagian SVG Anda -->
                </svg>
                <span class="ml-3">Dashboard</span>
              </a>
            </li>
          </router-link>
          <hr class="mt-3" />
          <br />
          <router-link to="/siswa/tugas" style="cursor: pointer">
            <li :class="setActivedNavClass(rl.tugas)">
              <a class="flex items-center p-2 text-gray-900 rounded-lg group">
                <svg
                  :class="setActivedNavClass(rl.tugas)"
                  class="flex-shrink-0 w-5 h-5 transition duration-75"
                  aria-hidden="true"
                  xmlns="http://www.w3.org/2000/svg"
                  fill="currentColor"
                  viewBox="0 0 18 18"
                >
                  <!-- Bagian SVG Anda -->
                </svg>
                <span
                  :class="setActivedNavClass(rl.tugas)"
                  class="flex-1 ml-3 whitespace-nowrap"
                  >Tugas</span
                >
                <span
                  class="inline-flex items-center justify-center px-2 ml-3 text-sm font-medium text-gray-800 bg-gray-100 rounded-full dark:bg-gray-700 dark:text-gray-300"
                  >Pro</span
                >
              </a>
            </li> </router-link
          ><br />

          <button
            style="width: 100%"
            class="bg-white hover:bg-white text-black font-bold py-2 px-4 rounded"
            @click="logouts"
          >
            Logout
          </button>
        </ul>
      </div>
    </aside>
  </div>
</template>

<!-- Sisa dari kode Anda -->

<script>
import { ref } from "vue";
import { mapActions, mapState } from "vuex";
export default {
  props: {
    idSiswa: Number,
  },
  computed: {
    siswa() {
      return JSON.parse(localStorage.user);
    },
    ...mapState("navbar", ["navbarsiswa"]),
  },
  methods: {
    ...mapActions("navbar", ["fetchnavbarsiswa"]),
    ...mapActions("auth", ["logoutsiswa"]),
    showseed(params) {
      this.fetchnavbarsiswa(params);
    },
    logouts() {
      const log = confirm("Apakah yakin ingin Logout");
      if (log) {
        this.logoutsiswa();
        window.location.href = "/";
      }
    },
  },
  setup(props) {
    const rl = ref({ dashboard: false, tugas: false });
    if (props.idSiswa == 100) {
      rl.value.dashboard = true;
    }
    if (props.idSiswa == 101) {
      rl.value.tugas = true;
    }

    return {
      rl,
    };
  },
  data() {
    return {
      setActivedNavClass(e) {
        let txtClass = "";
        try {
          if (e) {
            txtClass = "bg-orange-300 rounded text-black text-black-500";
          } else {
            txtClass = "";
          }
        } catch (err) {
          console.log(err);
          return 0;
        } finally {
          return txtClass;
        }
      },
    };
  },
};
</script>
