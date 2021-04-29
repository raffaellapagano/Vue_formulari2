<template>
  <div>
    <div class="row">
        <div class="col md-6">
          <h1>Formulario</h1>
          <form @submit.prevent>
            <Name></Name>
            <Telephone />
            <CodigoPostal /> 
            <Email />
            <Password />
            <button type="button" class="btn btn-primary btn-lg ml-2" @click="registerValidate">Validar</button>
            <div class="error">
              <span class="text-danger" v-if="check"> Mínim de 6 i màxim de 13 dígits que contengui majúscules i minúscules.</span>
            </div>
            <button type="submit" class="btn btn-primary btn-lg ml-2">Enviar</button>
          </form>
        </div>
      </div>
  </div>
</template>

<script>
import Name from './Name.vue'
import Telephone from './Telephone.vue'
import CodigoPostal from './CodigoPostal.vue'
import Email from './Email.vue'
import Password from './Password.vue'

export default {
  name: 'Formulari',
  components: {
    Name,
    Telephone,
    CodigoPostal,
    Email,
    Password
  },
  data() {
      return{
        errores: 0,
        check: "",
      }
    },
    methods: {
        registerValidate: function(){
            this.errores = 
            if(this.errores == 0){
                this.check = false;
                alert("Todo ok")
            }else{
                this.check = true;
            }
        }
    }
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.error{
    height: 30px;
}
</style>
