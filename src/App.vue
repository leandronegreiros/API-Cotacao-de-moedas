<template>
  <div class="container grid-ls my-2 py-2">
    <div class="card">
      <div class="cad-header">
        <div class="h4">Todas as moedas</div>
        <div class="cad-body">
          <ListQuotes :quotes="quotes"/>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { onMounted, reactive, toRefs } from 'vue'
import api from '@/services/api'
import ListQuotes from './components/ListQuotes'

export default { 
  name: "App",
  components: { ListQuotes },

  setup() {
    
    const data = reactive({
      quotes: {},
      test: ''
    })

    onMounted(async () =>{
      const response = await api.all();
      data.quotes = response.data
    })

    return { ...toRefs(data) }
  } 
}
</script>

