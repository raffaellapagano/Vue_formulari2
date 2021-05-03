<template>
  <div>
    <div class="row">
        <div class="col md-6">
          <h1 class="text-success">Formulario</h1>
          <form @submit.prevent="SendForm">
            <Name @check="validName = $event"></Name>
            <Telephone @check="validTel = $event"/>
            <CodigoPostal @check="validCp = $event"/> 
            <Email @check="validEmail = $event"/>
            <Password @check="validPassword = $event"/>
            <hr>
            <div class="error">
              <span class="text-danger" v-if="check">Datos incorrectos</span>
            </div>
            <div class="error">
            <button type="button" class="btn btn-primary btn-lg ml-2" @click="RegisterValidate">Validar</button>
            <button type="submit" class="btn btn-primary btn-lg ml-2">Enviar</button>
            </div>
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
        check: "",
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
                this.check = true;
                alert("Corregir los datos");
            }else if(this.validName === "" || this.validTel === "" || this.validCp === "" || this.validEmail === ""){
                this.check = true;
                alert("Llenar todos los campos");
            }else{
              this.check = false;
                alert("Datos correctos");
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
