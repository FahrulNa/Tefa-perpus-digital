<template>
  <div class="content">
      <div class="container-fluid">
          <nuxt-link to="/buku">
              <button type="button" class="btn btn-outline-dark btn-lg mt-4">KEMBALI</button></nuxt-link>
                  <h2 class="text-center my-4">RINCIAN BUKU</h2>
          <div class="row d-flex justify-content-center flex-md-wrap" style="padding-top: 190px;">
              <div class="col-3 ">
                  <img class="row img-fluid" src="@/assets/img/cover3.png" alt="" style="width: 250px;">
                  <div class="row">
                  </div>
              </div>
              <div class="col-8">
                  <div class="row">
                      <h1>172 DAYS</h1>
                  </div>
                  <div class="row">
                        <h4>PENULIS :- </h4>
                        <h4>PENERBIT : - </h4>
                        <h4>TAHUN TERBIT: - </h4>
                        <h4>RAK: - </h4>
                        <h4>KATEGORI: - </h4>
                        <h4>DESKRIPSI: - </h4>
                  </div>
                  <div class="row">
                  </div>
              </div>
          </div>
      </div>
      </div>
</template>
<script setup>
</script>
<style scoped>
.content {
  background-image:linear-gradient(#808080,#ffffff);
  background-size: cover;
  width: 100%;
  height: 100vh;
  font-family: '';
  color: black;
}
</style>