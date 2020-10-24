<template>
  <div>
    
    <h1>Productos de la Orden de Compra {{$route.query.numero}}</h1>
    

    <b-table striped hover :items="productos"></b-table>

    <b-form @submit.prevent="agregarProducto" inline  class="ml-5">
    <label class="sr-only2" for="inline-form-input-name">SKU:</label>
    <b-input
      id="inline-form-input-name"
      class="mb-2 mr-sm-2 mb-sm-0"
      placeholder="SKU"
      v-model="form.sku"
      required
      pattern="[0-9]*"
      title="SOLO NUMEROS"
    ></b-input>

    <label class="sr-only2" for="inline-form-input-name">NOMBRE:</label>
    <b-input
      id="inline-form-input-name"
      class="mb-2 mr-sm-2 mb-sm-0"
      v-model="form.nombre"
      required
      
      
    ></b-input>
    <label class="sr-only2" for="inline-form-input-name">CANTIDAD:</label>
    <b-input
      id="inline-form-input-name"
      class="mb-2 mr-sm-2 mb-sm-0"
      v-model="form.cantidad"
      required
      pattern="[0-9]*"
      title="SOLO NUMEROS"
    ></b-input>

    <label class="sr-only2" for="inline-form-input-name">PRECIO:</label>
    <b-input
      id="inline-form-input-name"
      class="mb-2 mr-sm-2 mb-sm-0"
      v-model="form.precio"
      required
      pattern="[0-9]*"
      title="SOLO NUMEROS"
    ></b-input>

    <b-button type="submit" class="colorBase">Agregar</b-button>
  </b-form>

  </div>

</template>

<script>
export default {
  // props:[usk, nombre],
  created() {
    this.datosProducto();
  },
  data() {
    return {
      // producto: this.$route.query.productos,
      productos: [],
      form: {
        sku: '',
        nombre: '',
        cantidad: '',
        precio: ''
      }
    }
  },
  methods: {
    datosProducto() {
      this.$route.query.productos.forEach(producto => {
        this.productos.push({
          sku: producto.sku,
          nombre: producto.name,
          cantidad: producto.quantity,
          precio: producto.price
        })
      });
    },
    agregarProducto(){
      this.productos.push(this.form);
      
      // if(this.form.sku !== '' || this.form.sku !== '' || this.form.cantidad !== '' || this.form.precio !== ''){

      //   this.productos.push(this.form);
      // }else{
      //   alert('llenar todos los cmpos');
      // }
    }
  },
}
</script>
<style >
  .colorBase{
    background: rgb(9,83,121);
    background: linear-gradient(135deg, rgba(9,83,121,1) 34%, rgba(8,208,249,1) 100%);
  }

</style>