<template>
  <div>
    <div class="row">
        <div class="col md-6 formulario">
          <h1>Formulario</h1>
          <form @submit.prevent>
            <Name @check="validName = $event"></Name>
            <Telephone @check="validTel = $event"/>
            <CodigoPostal @check="validCp = $event"/> 
            <Email @check="validEmail = $event"/>
            <Password @check="validPassword = $event"/>
            <button type="button" class="btn btn-primary btn-lg ml-2" @click="RegisterValidate">Validar</button>
            <div class="error">
              <span class="text-danger" v-if="check"> Datos incorrectos</span>
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
        validName: "",
        validTel: "",
        validCp: "",
        validEmail: "",
        validPassword: ""
      }
    },
    methods: {
        RegisterValidate(){
          
            if(this.validName || this.validTel || this.validCp || this.validEmail || this.validPassword || this.validPassword){
                alert("No");
            }else if(this.validName === "" || this.validTel === "" || this.validCp === "" || this.validEmail === "" || this.validPassword === "" || this.validPassword === ""){
                alert("Llenar todos los campos");
            }else{
                alert("Ok");
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
    height: 10px;
}
.formulario{
  height: 50%;
}
</style>
