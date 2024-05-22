<template>
  <div class="content">
    <div class="container-fluid">
      <div class="row">
        <div class="col-lg-12">
          <nuxt-link to="/pengunjung">
            <button type="button" class="btn btn-outline-dark mt-4 btn-lg">KEMBALI</button>
          </nuxt-link>
            <h2 class="text-center my-4">RAK BUKU</h2>
            <form @submit.prevent="getBooks" class="col mb-3">
              <div class="input-group flex-nowrap rounded">
                <input v-model="keyword" type="search" class="form-control from-control-lg rounded-5" placeholder="Cari..." aria-label="Search" @input="getbooks" />
              </div>
            </form>
            <div class="my-3">menampilkan {{ books.length }} buku dari {{ books.length }}</div>
          </div>
        </div>
          <div class="row">
              <div v-for="(book,i) in books" :key="i" class="col">
                  <div class="card mb-3 col-lg-2 col-2">
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
</template>
<script setup>
const supabase= useSupabaseClient()

const keyword = ref('')
const books = ref([])

const getbooks = async () => {
  const { data ,error } = await supabase
  .from('buku')
  .select(`*, kategori(*)`)
  .ilike("judul", `%${keyword.value}%`)
  .order('id')
  if(data) books.value = data
}

onMounted(() =>{
  getbooks()
})
</script>
<style scoped>
.content{
  background-image: linear-gradient(#808080,#ffffff);
  font-family: "";
}
.card-body {
  width: 220px;
  height: 20em;
  padding: 0;
}
.cover {
  width: 220px;
  height: 100%;
  object-fit: cover;
  object-position: 0 30;
}

</style>