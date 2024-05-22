<template>
    <div class="content">
        <div class="container-fluid">
            <nuxt-link to="/buku">
                <button type="button" class="btn btn-outline-dark btn-lg mt-4">KEMBALI</button></nuxt-link>
                    <h2 class="text-center my-4">RINCIAN BUKU</h2>
            <div class="row d-flex justify-content-center flex-md-wrap" style="padding-top: 190px;">
                <div class="col-3 ">
                        <img :src="buku?.cover"  class="cover row img-fluid" alt="cover buku"   style="width: 250px;">
                </div>
                <div class="col-8">
                    <div class="row">
                        <h1 class="text start text-center my-4">{{ buku?.judul }}</h1>
                    </div>
                        <div class="row">
                            <h2>PENULIS: {{ buku?.penulis }}</h2>
                            <h2>PENERBIT: {{ buku?.penerbit }}</h2>
                            <h2>TAHUN TERBIT: {{ buku?.tahun_terbit }}</h2>
                            <h2>RAK: {{ buku?.rak }}</h2>
                            <h2>KATEGORI: {{ buku?.kategori_buku?.nama }}</h2>
                            <h2>DESKRIPSI: {{ buku?.deskripsi }}</h2>                    
                        </div>
                </div>
            </div>
        </div>
    </div>
</template>
<script setup>
import { onMounted } from 'vue';

const supabase = useSupabaseClient()
const route = useRoute()
const buku = ref()
const kategories = ref ([])

const getBookByid = async () => {
    const { data, error } = await supabase
    .from('buku')
    .select(`*, kategori_buku(*)`)
    .eq('id', route.params.id)
    .maybeSingle()
    if (error) throw error
    if(data) buku.value = data
}

const getKategori = async () => {
    const { data, error } = await supabase
    .from('kategori_buku')
    .select('*')
    if(data) kategories.value = data
}


onMounted(() => {
    getBookByid()
    getKategori()
})

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