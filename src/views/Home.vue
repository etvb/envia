<template>
  <div class="home">
    <h1>Ordenes de Compra</h1>
    <OrdenesCompras />
  </div>
</template>

<script>
// @ is an alias to /src
import OrdenesCompras from '@/components/OrdenesCompras'

export default {
  name: 'Home',
  components: {
    OrdenesCompras
  }
}
</script>
