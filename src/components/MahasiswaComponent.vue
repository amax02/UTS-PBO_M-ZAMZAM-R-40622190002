<template>
  <div class="container">
    <div class="card m-3 p-5">
      <h4>Entry Data Mahasiswa</h4>
      <div class="form-group">
        <div class="mb-3">
          <label for="npm">NPM</label>
          <input
            v-model="npm"
            class="form-control"
            id="npm"
            name="npm"
            type="text"
          />
        </div>
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
          <label for="ipk">IPK</label>
          <input
            v-model="ipk"
            class="form-control"
            id="ipk"
            name="ipk"
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
      <h4>Data Mahasiswa</h4>
      <div class="table-responsive w-100">
        <table class="table-responsive table-hover table-bordered w-100">
          <tr>
            <th>Nama</th>
            <th>NPM</th>
            <th>IPK</th>
          </tr>
          <tr v-for="(mahasiswa, index) in submittedData" :key="index">
            <td>{{ mahasiswa.name }}</td>
            <td>{{ mahasiswa.npm }}</td>
            <td>{{ mahasiswa.ipk }}</td>
          </tr>
        </table>
      </div>
    </div>
  </div>
</template>

<script>
class Mahasiswa {
  constructor(name, npm, ipk) {
    this.name = name;
    this.npm = npm;
    this.ipk = ipk;
  }
}
export default {
  data() {
    return {
      name: "",
      npm: "",
      ipk: "",
      submittedData: [], // Array to store submitted data
    };
  },
  methods: {
    simpan() {
      if (!this.name && !this.npm && !this.ipk) {
        alert("Data NAMA & NPM & IPK Belum diisi");
        return false;
      }
      if (!this.npm) {
        alert("Data NPM Belum diisi");
        return false;
      }

      if (!this.name) {
        alert("Data Nama Belum diisi");
        return false;
      }

      if (!this.ipk) {
        alert("Data IPK Belum diisi");
        return false;
      }

      if (this.ipk < 1 || this.ipk > 4) {
        alert("Data IPK Harus diantara 1 dan 4");
        return false;
      }

      const mahasiswa = new Mahasiswa(this.name, this.npm, this.ipk);
      this.submittedData.push(mahasiswa);
      alert("Data Mahasiswa (" + mahasiswa.name + ") Berhasil disimpan");
      this.name = "";
      this.npm = "";
      this.ipk = "";
    },
  },
};
</script>

<style scoped>
/* Add styling for each component, if needed */
</style>
