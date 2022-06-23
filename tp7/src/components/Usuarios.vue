<template>

<section class="jumbotron">

  <h3 v-if="!usuarios.length" class="alert alert-warning">
      No hay usuarios disponibles
  </h3>

  <div v-else class="class table-responsive">
        <table class="class table table-dark">
          <tr>
            <th>Nombre</th>
            <th>Edad</th>
            <th>Email</th>
          </tr>
          <tr v-for="(usuario, index) in usuarios" :key="index">
            <td> {{usuario.name}}</td>
            <td>{{usuario.age}}</td>
            <td>{{usuario.email}}</td>


          </tr>

      </table>
  </div>
  <br>
  <div class="col text-center">
      <button style="center " class="btn btn-primary mr-2" @click="ir()">IR AL FORMULARIO</button>
  </div>
  
  
</section>
</template>

<script>

  export default  {
    name: 'src-components-usuarios',
    props: [],
    created () {
      this.axios(this.url)
          .then(({ data:respuesta }) => {
            this.usuarios = respuesta
          })
          .catch( error => console.error('Error en Axios:', error))
    },
    mounted () {

    },
    data () {
      return {
        url: 'https://62b47909530b26da4cbf650c.mockapi.io/users',
        usuarios: []
      }
    },
    methods: {
      ir() {
        this.$router.push({
          path: '/formulario'
        })
      }
    },
    computed: {

    }
}


</script>

<style scoped lang="css">
  .src-components-usuarios {

  }
  .jumbotron {
      background-color: rgb(5, 41, 43);
      color: white;
  }
</style>
