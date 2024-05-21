<template>
    <div class="content">
        <div class="container-fluid">
            <nuxt-link to="/buku">
                <button type="button" class="btn btn-outline-dark btn-lg mt-4">KEMBALI</button></nuxt-link>
                    <h2 class="text-center my-4">RINCIAN BUKU</h2>
            <div class="row d-flex justify-content-center flex-md-wrap" style="padding-top: 190px;">
                <div class="col-3 ">
                    <img :src="buku.cover"  class="cover row img-fluid" alt="cover buku"   style="width: 250px;">
                    <div class="row">
                    </div>
                </div>
                <div class="col-8">
                    <div class="row">
                        <h1 class="text start text-center my-4">{{ buku.judul }}</h1>
                    </div>
                    <div class="row">
                    <div class="badge bg-primary p-2">{{ buku.kategori }}</div>
                        <ul class="list-group list-group-flush">
                            <li class="list-group-item">PENULIS: {{ buku.penulis }}</li>
                            <li class="list-group-item">PENERBIT: {{ buku.penerbit }}</li>
                            <li class="list-group-item">DESKRIPSI: {{ buku.deskripsi }}</li>
                            <li class="list-group-item">TAHUN TERBIT</li>
                        </ul>                       
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