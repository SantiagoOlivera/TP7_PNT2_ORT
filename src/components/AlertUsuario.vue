<template lang="html">

  <section class="src-components-alert-usuario">
    <div class="container">
      <h1>Alert Usuario</h1>
      <div class="alert alert-danger" role="alert">
          {{ mostrarMensaje }}
      </div>
    </div>
  </section>

</template>

<script lang="js">
  export default  {
    name: 'src-components-alert-usuario',
    props: [],
    mounted () {
      this.getData();
    },
    data () {
      return {
          API_URL: "https://6366f216f5f549f052ce96e7.mockapi.io/TP_PNT2_ORT/TP7",
        data: [],
      }
    },
    methods: {
       getData(){
        this.axios.get(this.API_URL)
          .then( res => { 
              this.data = res.data; 
          })
          .catch(error => console.log(error));
      },
    },
    computed: {
      mostrarMensaje(){
        var msg = null;
        if(this.data.length === 0){
          msg = 'No hay usuarios registrados en MockApi!';
        }else{
          msg = `Hay en MockApi ${this.data.length} usuarios registrados!`;
        }
        return msg;
      }
    }
}
</script>

<style scoped>
  .src-components-alert-usuario {
  }
</style>
