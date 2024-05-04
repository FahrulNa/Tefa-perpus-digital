<script setup>
const supabase = useSupabaseClient()

const route = useRoute()
const buku = ref([])

const getBookById = async () => {
  const { data, error } = await supabase.from('buku').select(`*, kategori(*)`).eq('id', route.params.id).maybeSingle()
  if(data) buku.value = data
  console.log(buku.value)
}

onMounted(() =>{
  getBookById()
})

</script>