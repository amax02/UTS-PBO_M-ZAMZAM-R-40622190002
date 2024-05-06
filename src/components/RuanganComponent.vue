<template>
  <div class="container">
    <div class="card m-3 p-5">
      <h4>Entry Data Ruangan</h4>
      <div class="form-group">
        <div class="mb-3">
          <label for="name">Nama</label>
          <input
            v-model="name"
            class="form-control"
            id="name"
            name="name"
            type="text"
          />
        </div>
        <div class="mb-3">
          <label for="code">Kode</label>
          <input
            v-model="code"
            class="form-control"
            id="code"
            name="code"
            type="number"
          />
        </div>
        <div class="mb-3">
          <button class="btn btn-primary" @click="simpan">Submit</button>
        </div>
      </div>
    </div>

    <!-- Display submitted data -->
    <div class="card m-3 p-5">
      <h4>Data Ruangan</h4>
      <div class="table-responsive w-100">
        <table class="table-responsive table-hover table-bordered w-100">
          <tr>
            <th>Nama</th>
            <th>Kode</th>
          </tr>
          <tr v-for="(ruangan, index) in submittedData" :key="index">
            <td>{{ ruangan.name }}</td>
            <td>{{ ruangan.code }}</td>
          </tr>
        </table>
      </div>
    </div>
  </div>
</template>

<script>
class Ruangan {
  constructor(name, code) {
    this.name = name;
    this.code = code;
  }
}
export default {
  data() {
    return {
      name: "",
      npm: "",
      submittedData: [], // Array to store submitted data
    };
  },
  methods: {
    simpan() {
      if (!this.name && !this.code) {
        alert("Data NAMA & CODE Belum diisi");
        return false;
      }
      if (!this.name) {
        alert("Data Nama Belum diisi");
        return false;
      }

      if (!this.code) {
        alert("Data Kode Belum diisi");
        return false;
      }

      const ruangan = new Ruangan(this.name, this.code);
      this.submittedData.push(ruangan);
      alert("Data Ruangan (" + ruangan.name + ") Berhasil disimpan");
      this.name = "";
      this.npm = "";
      this.code = "";
    },
  },
};
</script>

<style scoped>
/* Add styling for each component, if needed */
</style>
