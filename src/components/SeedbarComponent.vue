<template>
  <aside
    style="background: #ff00ff"
    id="logo-sidebar"
    :class="
      navbar == true
        ? 'fixed  shadow-md top-0 left-0 z-40 w-64 h-screen pt-20 transition-transform bg-white border-r border-gray-200 sm:translate-x-0 dark:bg-gray-800 dark:border-gray-700'
        : 'fixed top-0 left-0 z-40 w-64 h-screen pt-20 transition-transform -translate-x-full bg-white border-r border-gray-200 sm:translate-x-0  shadow-xl border-0'
    "
    aria-label="Sidebar"
  >
    <div
      style="background: #ff00ff"
      clas
      class="h-full px-3 pb-4 overflow-y-auto dark:bg-gray-800"
    >
      <ul class="space-y-2 font-medium">
        <router-link to="/admin/dashboard">
          <li style="color: white" :class="setActivedNavClass(rl[1])">
            <a
              style="color: white"
              href="#"
              class="flex items-center p-2 text-gray-900 rounded-lg dark:text-white hover:bg-white-100 dark:hover:bg-gray-700 group"
            >
              <svg
                :class="setActivedNavClass(rl[1])"
                class="w-5 h-5 text-white transition duration-75 dark:text-gray-400"
                aria-hidden="true"
                xmlns="http://www.w3.org/2000/svg"
                fill="currentColor"
                viewBox="0 0 22 21"
              >
                <path
                  d="M16.975 11H10V4.025a1 1 0 0 0-1.066-.998 8.5 8.5 0 1 0 9.039 9.039.999.999 0 0 0-1-1.066h.002Z"
                />
                <path
                  d="M12.5 0c-.157 0-.311.01-.565.027A1 1 0 0 0 11 1.02V10h8.975a1 1 0 0 0 1-.935c.013-.188.028-.374.028-.565A8.51 8.51 0 0 0 12.5 0Z"
                />
              </svg>
              <span
                style="color:white "
                :class="setActivedNavClass(rl[1])"
                class="ml-3 text-white"
                >Dashboard</span
              >
            </a>
          </li>
        </router-link>
        <router-link to="/admin/siswa">
          <li :class="setActivedNavClass(rl[2])">
            <a
              href="#"
              style="color: white"
              class="flex items-center p-2 text-gray-900 rounded-lg dark:text-white hover:bg-white-100 dark:hover:bg-gray-700 group"
            >
              <svg
                style="color: white"
                :class="setActivedNavClass(rl[2])"
                class="flex-shrink-0 w-5 h-5 text-white transition duration-75 dark:text-gray-400 group-hover:text-gray-900 dark:group-hover:text-white"
                aria-hidden="true"
                xmlns="http://www.w3.org/2000/svg"
                fill="currentColor"
                viewBox="0 0 20 18"
              >
                <path
                  d="M14 2a3.963 3.963 0 0 0-1.4.267 6.439 6.439 0 0 1-1.331 6.638A4 4 0 1 0 14 2Zm1 9h-1.264A6.957 6.957 0 0 1 15 15v2a2.97 2.97 0 0 1-.184 1H19a1 1 0 0 0 1-1v-1a5.006 5.006 0 0 0-5-5ZM6.5 9a4.5 4.5 0 1 0 0-9 4.5 4.5 0 0 0 0 9ZM8 10H5a5.006 5.006 0 0 0-5 5v2a1 1 0 0 0 1 1h11a1 1 0 0 0 1-1v-2a5.006 5.006 0 0 0-5-5Z"
                />
              </svg>
              <span
                style="color: white"
                :class="setActivedNavClass(rl[2])"
                class="flex-1 ml-3 text-white whitespace-nowrap"
                >Siswa</span
              >
            </a>
          </li>
        </router-link>
          <!-- <router-link to="/admin/riwayat_tabungan">
            <li style="color: white" :class="setActivedNavClass(rl[3])">
              <a
                href="#"
                class="flex items-center p-2 text-gray-900 rounded-lg dark:text-white hover:bg-white-100 dark:hover:bg-gray-700 group"
              >
                <svg
                  style="color: white"
                  :class="setActivedNavClass(rl[3])"
                  class="flex-shrink-0 w-5 h-5 text-dark transition duration-75 dark:text-gray-400 group-hover:text-gray-900 dark:group-hover:text-white"
                  aria-hidden="true"
                  xmlns="http://www.w3.org/2000/svg"
                  fill="currentColor"
                  viewBox="0 0 20 18"
                >
                  <path
                    d="M14 2a3.963 3.963 0 0 0-1.4.267 6.439 6.439 0 0 1-1.331 6.638A4 4 0 1 0 14 2Zm1 9h-1.264A6.957 6.957 0 0 1 15 15v2a2.97 2.97 0 0 1-.184 1H19a1 1 0 0 0 1-1v-1a5.006 5.006 0 0 0-5-5ZM6.5 9a4.5 4.5 0 1 0 0-9 4.5 4.5 0 0 0 0 9ZM8 10H5a5.006 5.006 0 0 0-5 5v2a1 1 0 0 0 1 1h11a1 1 0 0 0 1-1v-2a5.006 5.006 0 0 0-5-5Z"
                  />
                </svg>
                <span
                  style="color: white"
                  :class="setActivedNavClass(rl[3])"
                  class="flex-1 ml-3 text-white whitespace-nowrap"
                  >Riwayat tabungan</span
                >
              </a>
            </li>
          </router-link> -->

        <router-link to="/admin/kelas">
          <li style="color: white" :class="setActivedNavClass(rl[4])">
            <a
              href="#"
              class="flex items-center p-2 text-gray-900 rounded-lg dark:text-white hover:bg-white-100 dark:hover:bg-gray-700 group"
            >
              <svg
                style="color: white"
                :class="setActivedNavClass(rl[4])"
                class="flex-shrink-0 w-5 h-5 text-dark transition duration-75 dark:text-gray-400 group-hover:text-gray-900 dark:group-hover:text-white"
                aria-hidden="true"
                xmlns="http://www.w3.org/2000/svg"
                fill="currentColor"
                viewBox="0 0 20 18"
              >
                <path
                  d="M14 2a3.963 3.963 0 0 0-1.4.267 6.439 6.439 0 0 1-1.331 6.638A4 4 0 1 0 14 2Zm1 9h-1.264A6.957 6.957 0 0 1 15 15v2a2.97 2.97 0 0 1-.184 1H19a1 1 0 0 0 1-1v-1a5.006 5.006 0 0 0-5-5ZM6.5 9a4.5 4.5 0 1 0 0-9 4.5 4.5 0 0 0 0 9ZM8 10H5a5.006 5.006 0 0 0-5 5v2a1 1 0 0 0 1 1h11a1 1 0 0 0 1-1v-2a5.006 5.006 0 0 0-5-5Z"
                />
              </svg>
              <span
                style="color: white"
                :class="setActivedNavClass(rl[4])"
                class="flex-1 ml-3 text-white whitespace-nowrap"
                >Kelas
              </span>
            </a>
          </li>
        </router-link>

        <router-link to="/admin/hari">
          <li style="color: white" :class="setActivedNavClass(rl[5])">
            <a
              href="#"
              class="flex items-center p-2 text-gray-900 rounded-lg dark:text-white hover:bg-white-100 dark:hover:bg-gray-700 group"
            >
              <svg
                style="color: white"
                :class="setActivedNavClass(rl[5])"
                class="flex-shrink-0 w-5 h-5 text-dark transition duration-75 dark:text-gray-400 group-hover:text-gray-900 dark:group-hover:text-white"
                aria-hidden="true"
                xmlns="http://www.w3.org/2000/svg"
                fill="currentColor"
                viewBox="0 0 20 18"
              >
                <path
                  d="M14 2a3.963 3.963 0 0 0-1.4.267 6.439 6.439 0 0 1-1.331 6.638A4 4 0 1 0 14 2Zm1 9h-1.264A6.957 6.957 0 0 1 15 15v2a2.97 2.97 0 0 1-.184 1H19a1 1 0 0 0 1-1v-1a5.006 5.006 0 0 0-5-5ZM6.5 9a4.5 4.5 0 1 0 0-9 4.5 4.5 0 0 0 0 9ZM8 10H5a5.006 5.006 0 0 0-5 5v2a1 1 0 0 0 1 1h11a1 1 0 0 0 1-1v-2a5.006 5.006 0 0 0-5-5Z"
                />
              </svg>
              <span
                style="color: white"
                :class="setActivedNavClass(rl[5])"
                class="flex-1 ml-3 text-white whitespace-nowrap"
                >Hari
              </span>
            </a>
          </li>
        </router-link>

        <router-link to="/admin/mata-pelajaran">
          <li style="color: white" :class="setActivedNavClass(rl[6])">
            <a
              href="#"
              class="flex items-center p-2 text-gray-900 rounded-lg dark:text-white hover:bg-white-100 dark:hover:bg-gray-700 group"
            >
              <svg
                style="color: white"
                :class="setActivedNavClass(rl[6])"
                class="flex-shrink-0 w-5 h-5 text-dark transition duration-75 dark:text-gray-400 group-hover:text-gray-900 dark:group-hover:text-white"
                aria-hidden="true"
                xmlns="http://www.w3.org/2000/svg"
                fill="currentColor"
                viewBox="0 0 20 18"
              >
                <path
                  d="M14 2a3.963 3.963 0 0 0-1.4.267 6.439 6.439 0 0 1-1.331 6.638A4 4 0 1 0 14 2Zm1 9h-1.264A6.957 6.957 0 0 1 15 15v2a2.97 2.97 0 0 1-.184 1H19a1 1 0 0 0 1-1v-1a5.006 5.006 0 0 0-5-5ZM6.5 9a4.5 4.5 0 1 0 0-9 4.5 4.5 0 0 0 0 9ZM8 10H5a5.006 5.006 0 0 0-5 5v2a1 1 0 0 0 1 1h11a1 1 0 0 0 1-1v-2a5.006 5.006 0 0 0-5-5Z"
                />
              </svg>
              <span
                style="color: white"
                :class="setActivedNavClass(rl[6])"
                class="flex-1 ml-3 text-white whitespace-nowrap"
              >
                Mata-Pelajaran
              </span>
            </a>
          </li>
        </router-link>

        <router-link to="/admin/tugas">
          <li style="color: white" :class="setActivedNavClass(rl[7])">
            <a
              href="#"
              class="flex items-center p-2 text-gray-900 rounded-lg dark:text-white hover:bg-white-100 dark:hover:bg-gray-700 group"
            >
              <svg
                style="color: white"
                :class="setActivedNavClass(rl[7])"
                class="flex-shrink-0 w-5 h-5 text-dark transition duration-75 dark:text-gray-400 group-hover:text-gray-900 dark:group-hover:text-white"
                aria-hidden="true"
                xmlns="http://www.w3.org/2000/svg"
                fill="currentColor"
                viewBox="0 0 20 18"
              >
                <path
                  d="M14 2a3.963 3.963 0 0 0-1.4.267 6.439 6.439 0 0 1-1.331 6.638A4 4 0 1 0 14 2Zm1 9h-1.264A6.957 6.957 0 0 1 15 15v2a2.97 2.97 0 0 1-.184 1H19a1 1 0 0 0 1-1v-1a5.006 5.006 0 0 0-5-5ZM6.5 9a4.5 4.5 0 1 0 0-9 4.5 4.5 0 0 0 0 9ZM8 10H5a5.006 5.006 0 0 0-5 5v2a1 1 0 0 0 1 1h11a1 1 0 0 0 1-1v-2a5.006 5.006 0 0 0-5-5Z"
                />
              </svg>
              <span
                style="color: white"
                :class="setActivedNavClass(rl[7])"
                class="flex-1 ml-3 text-white whitespace-nowrap"
              >
                Tugas
              </span>
            </a>
          </li>
        </router-link>

        <li>
          <a 
            href="#"
            @click="logouts"
            class="flex items-center p-2 text-gray-900 rounded-lg dark:text-white hover:bg-white-100 dark:hover:bg-gray-700 group"
          >
            <svg
              class="flex-shrink-0 w-5 h-5 text-white transition duration-75"
              aria-hidden="true"
              xmlns="http://www.w3.org/2000/svg"
              fill="currentColor"
              viewBox="0 0 20 20"
            >
              <path
                d="M5 5V.13a2.96 2.96 0 0 0-1.293.749L.879 3.707A2.96 2.96 0 0 0 .13 5H5Z"
              />
              <path
                d="M6.737 11.061a2.961 2.961 0 0 1 .81-1.515l6.117-6.116A4.839 4.839 0 0 1 16 2.141V2a1.97 1.97 0 0 0-1.933-2H7v5a2 2 0 0 1-2 2H0v11a1.969 1.969 0 0 0 1.933 2h12.134A1.97 1.97 0 0 0 16 18v-3.093l-1.546 1.546c-.413.413-.94.695-1.513.81l-3.4.679a2.947 2.947 0 0 1-1.85-.227 2.96 2.96 0 0 1-1.635-3.257l.681-3.397Z"
              />
              <path
                d="M8.961 16a.93.93 0 0 0 .189-.019l3.4-.679a.961.961 0 0 0 .49-.263l6.118-6.117a2.884 2.884 0 0 0-4.079-4.078l-6.117 6.117a.96.96 0 0 0-.263.491l-.679 3.4A.961.961 0 0 0 8.961 16Zm7.477-9.8a.958.958 0 0 1 .68-.281.961.961 0 0 1 .682 1.644l-.315.315-1.36-1.36.313-.318Zm-5.911 5.911 4.236-4.236 1.359 1.359-4.236 4.237-1.7.339.341-1.699Z"
              />
            </svg>
            <span class="flex-1 ml-3 text-white whitespace-nowrap">Logout</span>
          </a>
        </li>
      </ul>
    </div>
  </aside>
</template>
<script>
import { ref } from "vue";
import { mapState, mapActions } from "vuex";
export default {
  computed: {
    ...mapState("navbar", ["navbar"]),
  },
  methods: {
    ...mapActions("auth", ["logout"]),
    logouts() {
      let cnfrm = confirm("Apakah Anda yakin ingin melakukan logout?");
      if (cnfrm) {
        this.logout();
        window.location.href = "/admin";
      }
    },
  },
  props: {
    idMenu: Number,
  },
  setup(props) {
    const rl = ref([false, false, false, false]);

    if (props.idMenu == 0) {
      rl.value[0] = true;
    }
    if (props.idMenu == 1) {
      rl.value[1] = true;
    }
    if (props.idMenu == 2) {
      rl.value[2] = true;
    }
    if (props.idMenu == 3) {
      rl.value[3] = true;
    }
    if (props.idMenu == 4) {
      rl.value[4] = true;
    }
    if (props.idMenu == 5) {
      rl.value[5] = true;
    }
    if (props.idMenu == 6) {
      rl.value[6] = true;
    }
    if (props.idMenu == 7) {
      rl.value[7] = true;
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
            txtClass = "bg-purple-300 rounded text-black text-black-500";
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
