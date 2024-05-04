<template>
  <div class="content">
    <div class="container-fluid">
      <div class="row">
        <div class="col-lg-12">
          <nuxt-link to="/pengunjung">
          <button type="button" class="btn btn-outline-dark mt-4 btn-lg">KEMBALI</button></nuxt-link>
          <h2 class="text-center my-4">RAK BUKU</h2>
          <form @submit.prevent="getBooks">
            <input v-model="keyword" type="search" class="form-control form-control-lg rounded-5" placeholder="Cari..." >
          </form>
        <div class="my-3">menampilkan 4 dari 4</div>
          <div class="row">
              <div class="col-lg-2">
                  <div v-for="(book,i) in books" :key="i" class="card mb-3">
                    <nuxt-link :to="`/buku/${book.id}`">
                      <div class="card-body">
                        <img :src="book.cover" class="cover" alt="cover">
                      </div>
                    </nuxt-link>
                  </div>
              </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script setup>
const supabase= useSupabaseClient ()
const books = ref([])

const getbooks = async () => {
  const { data ,error } = await supabase.from('buku').select(`*, kategori(*)`).order('id')
  if(data) books.value = data
}

onMounted(() =>{
  getbooks()
})

const keyword = ref('')
const getBooks = async () => {
  const { data, error } = await supabase.from('buku').select(`*, kategori(*)`)
  if(data) books.value = data
}

</script>
<style scoped>
.content{
  background-image: linear-gradient(#808080,#ffffff);
  font-family: "";
}
.card-body {
  width: 100%;
  height: 20em;
  padding: 0;
}
.cover {
  width: 100%;
  height: 100%;
  object-fit: cover;
  object-position: 0 30;
}

</style>