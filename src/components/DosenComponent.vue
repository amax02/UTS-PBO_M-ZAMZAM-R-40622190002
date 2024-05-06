<template>
  <div class="card m-3 p-5">
    <h4>Entry Data Dosen</h4>
    <div class="form-group">
      <div class="mb-3">
        <label for="nidn">NIDN</label>
        <input v-model="nidn" class="form-control" id="nidn" name="nidn" type="text">
      </div>
      <div class="mb-3">
        <label for="name">Nama</label>
        <input v-model="name" class="form-control" id="name" name="name" type="text">
      </div>
      <div class="mb-3">
        <button class="btn btn-primary" @click="simpan">Submit</button>
      </div>
    </div>
  </div>

  <!-- Display submitted data -->
  <div class="card m-3 p-5">
    <h4>Data Dosen</h4>
    <div class="table-responsive w-100">
      <table class="table-responsive table-hover table-bordered w-100">
        <tr>
          <th>Nama</th>
          <th>NIDN</th>
        </tr>
        <tr v-for="(ruangan, index) in submittedData" :key="index">
            <td>{{ ruangan.name }}</td>
            <td>{{ ruangan.nidn }}</td>
        </tr>
      </table>
    </div>
  </div>
</template>
  
<script>
class Dosen {
  constructor(name, nidn) {
    this.name = name;
    this.nidn = nidn;
  }
 
}
export default {
  data() {
    return {
      name: '',
      nidn: '',
      submittedData: [] // Array to store submitted data
    }
  },
  methods: {
    simpan() {
     

      if(!this.nidn){
        alert("Data NIDN Belum diisi");
        return false;
      }

      if(!this.name){
        alert("Data Nama Belum diisi");
        return false;
      }

      const dosen = new Dosen(this.name, this.nidn);
      this.submittedData.push(dosen);
      alert("Data Dosen ("+dosen.name+") Berhasil disimpan");
      this.name = '';
      this.nidn = '';
    }
  }
};
</script>
  
<style scoped>
/* Add styling for each component, if needed */
</style>
