<template>
  <div class="p-4 sm:ml-64">
    <div class="p-4 rounded-lg dark:border-gray-700">
      <div
        class="bg-orange-100 shadow-sm border-l-4 border-orange-500 text-orange-700 p-4"
        role="alert"
      >
        <p class="font-bold">Selamat Datang</p>
        <p>Hallo , Selamat Datang Dan Selamat Melihat Dan Mengerjakan </p>
      </div>
      <br />
      <div
        class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-4"
      >
        <!-- Card 1 -->
        <div class="bg-white rounded-lg p-4 shadow-md">
          <span class="text-xl font-semibold">Senin</span>
          &nbsp;&nbsp;
          <span class="mt-2 text-gray-700">  </span>
          <div class="mt-2">
            <b style="font-family: sans-serif; font-size: 10px; color: green;"> Yang Sudah Di Kerjakan : {{seninDikerjakan() }} </b><br>
               <b style="font-family: sans-serif; font-size: 10px; color: red;"> Yang Belum Di Kerjakan : {{ seninBelumDikerjakan()  }} </b>
          </div>
        </div>
        <div class="bg-white rounded-lg p-4 shadow-md">
          <span class="text-xl font-semibold">Selasa</span>
          &nbsp;&nbsp;
          <span class="mt-2 text-gray-700"></span>
          <div class="mt-2">
            <b style="font-family: sans-serif; font-size: 10px; color: green;"> Yang Sudah Di Kerjakan : {{ selasaDikerjakan() }} </b><br>
            <b style="font-family: sans-serif; font-size: 10px; color: red;"> Yang Belum Di Kerjakan : {{ selasaBelumDikerjakan() }} </b>
          </div>
        </div>
        <div class="bg-white rounded-lg p-4 shadow-md">
          <span class="text-xl font-semibold">Rabu</span>
          &nbsp;&nbsp;
          <span class="mt-2 text-gray-700"> </span>
          <div class="mt-2">
               <b style="font-family: sans-serif; font-size: 10px; color: green;"> Yang Sudah Di Kerjakan : {{ RabuDikerjakan() }} </b><br>
               <b style="font-family: sans-serif; font-size: 10px; color: red;"> Yang Belum Di Kerjakan : {{ RabuBelumDikerjakan() }} </b>
          </div>
        </div>
        <div class="bg-white rounded-lg p-4 shadow-md">
          <span class="text-xl font-semibold">Kamis</span>
          &nbsp;&nbsp;
          <span class="mt-2 text-gray-700"> {{ kamis }} </span>
          <div class="mt-2">
            <b style="font-family: sans-serif; font-size: 10px; color: green;"> Yang Sudah Di Kerjakan : {{ KamisDikerjakan() }} </b><br>
               <b style="font-family: sans-serif; font-size: 10px; color: red;"> Yang Belum Di Kerjakan : {{ KamisBelumDikerjakan() }} </b>
          </div>
        </div>
        <div class="bg-white rounded-lg p-4 shadow-md">
          <span class="text-xl font-semibold">Jumat</span>
          &nbsp;&nbsp;
          <span class="mt-2 text-gray-700"> {{ jumat }} </span>
          <div class="mt-2">
            <b style="font-family: sans-serif; font-size: 10px; color: green;"> Yang Sudah Di Kerjakan :  {{ JumatDikerjakan() }}</b><br>
               <b style="font-family: sans-serif; font-size: 10px; color: red;"> Yang Belum Di Kerjakan : {{ JumatBelumDikerjakan() }} </b>
          </div>
        </div>
        <div class="bg-white rounded-lg p-4 shadow-md">
          <span class="text-xl font-semibold">Sabtu</span>
          &nbsp;&nbsp;
          <span class="mt-2 text-gray-700"> {{ sabtu }} </span>
          <div class="mt-2">
            <b style="font-family: sans-serif; font-size: 10px; color: green;"> Yang Sudah Di Kerjakan : {{ SabtuDikerjakan() }} </b><br>
               <b style="font-family: sans-serif; font-size: 10px; color: red;"> Yang Belum Di Kerjakan : {{ SabtuBelumDikerjakan() }} </b>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import { ref } from "vue";
import { onMounted } from "vue";
import { mapState } from "vuex";
export default {
  computed: {
    ...mapState("hari", ["hari"]),
    ...mapState("tugas_siswa", ["tugas_siswa"]),
  },
  mounted() {
    this.$store.dispatch("hari/fecthari");
    this.$store.dispatch("tugas_siswa/fetchtugasiswa");;
  },
  methods: {
    seninDikerjakan() {
          const seninTugas = this.tugas_siswa.filter((element) => element.hari === "Senin" && element.id_user === 1 && element.status == 1);
          return seninTugas.length;
    },
    seninBelumDikerjakan(){
      const seninTugas = this.tugas_siswa.filter((element) => element.hari === "Senin" && element.id_user === 1 && element.status == 0);
      return seninTugas.length;
    },
    selasaDikerjakan() {
          const selasaTugas = this.tugas_siswa.filter((element) => element.hari === "Selasa" && element.id_user === 1 && element.status == 1);
          return selasaTugas.length;
    },
    selasaBelumDikerjakan() {
          const selasaTugas = this.tugas_siswa.filter((element) => element.hari === "Selasa" && element.id_user === 1 && element.status == 0);
          return selasaTugas.length;
    },
    RabuDikerjakan() {
          const rabuTugas = this.tugas_siswa.filter((element) => element.hari === "Rabu" && element.id_user === 1 && element.status == 1);
          return rabuTugas.length;
    },
    RabuBelumDikerjakan() {
          const rabuTugas = this.tugas_siswa.filter((element) => element.hari === "Rabu" && element.id_user === 1 && element.status == 0);
          return rabuTugas.length;
    },
    KamisDikerjakan() {
          const KamisTugas = this.tugas_siswa.filter((element) => element.hari === "Kamis" && element.id_user === 1 && element.status == 1);
          return KamisTugas.length;
    },
    KamisBelumDikerjakan() {
          const KamisTugas = this.tugas_siswa.filter((element) => element.hari === "Kamis" && element.id_user === 1 && element.status == 0);
          return KamisTugas.length;
    },
    JumatDikerjakan() {
          const JumatTugas = this.tugas_siswa.filter((element) => element.hari === "Jumat" && element.id_user === 1 && element.status == 1);
          return JumatTugas.length;
    },
    JumatBelumDikerjakan() {
          const JumatTugas = this.tugas_siswa.filter((element) => element.hari === "Jumat" && element.id_user === 1 && element.status == 0);
          return JumatTugas.length;
    },
    SabtuDikerjakan() {
          const SabtuTugas = this.tugas_siswa.filter((element) => element.hari === "Sabtu" && element.id_user === 1 && element.status == 1);
          return SabtuTugas.length;
    },
    SabtuBelumDikerjakan() {
          const SabtuTugas = this.tugas_siswa.filter((element) => element.hari === "Sabtu" && element.id_user === 1 && element.status == 0);
          return SabtuTugas.length;
    },


  },
  setup(props, context) {
    onMounted(() => {
      try {
        context.emit("id-menu", "siswa");
        context.emit("id-siswa", 100);
      } catch (error) {
        console.log(error);
      }
    });
  },
};
</script>
