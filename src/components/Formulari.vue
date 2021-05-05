<template>
  <div>
    <div class="row">
        <div class="col md-6">
          <h1 class="text-success">Formulario</h1>
          <form @submit.prevent="RegisterValidate">

            <InputComponent 
              :label="labelText.labelName"
              :type= "'text'"
              :idInput= "'idName'"
              :msgInput="msnText.msnString"
              :require="true"
              @ReturnValidation="AddValidation"></InputComponent>

              <InputComponent 
              :label="labelText.labelTel"
              :type= "'text'"
              :idInput= "'idTel'"
              :msgInput="msnText.msnTel"
              :require="true"
              @ReturnValidation="AddValidation"></InputComponent>

              <InputComponent 
              :label="labelText.labelCP"
              :type= "'text'"
              :idInput= "'idCP'"
              :msgInput="msnText.msnCP"
              :require="true"
              @ReturnValidation="AddValidation"></InputComponent>

              <InputComponent 
              :label="labelText.labelEmail"
              :type= "'email'"
              :idInput= "'idEmail'"
              :msgInput="msnText.msnEmail"
              :require="true"
              @ReturnValidation="AddValidation"></InputComponent>

              <InputComponent 
              :label="labelText.labelPass"
              :type= "'password'"
              :idInput= "'idPass'"
              :msgInput="msnText.msnPass"
              :require="true"
              @ReturnValidation="AddValidation"
              @Password="checkPassword"></InputComponent>

              <InputComponent 
              :label="labelText.labelPass2"
              :type= "'password'"
              :idInput= "'idPass2'"
              :msgInput="msnText.msnPass2"
              :require="true"
              :checkPassword2="checkPassword"
              @ReturnValidation="AddValidation"></InputComponent>

              
            <hr>
            
            <div class="error" v-if="errors.length">
                <ul>
                  <li v-for="error in errors" :key="error"></li>
                </ul>
              </div>
              <div>
            <button type="button" class="btn btn-primary btn-lg ml-2">Validar</button>
            <button type="submit" class="btn btn-primary btn-lg ml-2">Enviar</button>
            </div>
          </form>
        </div>
      </div>
  </div>
</template>

<script>
import InputComponent from './InputComponent.vue'

export default {
  name: 'Formulari',
  components: {
    InputComponent
  },
  data() {
      return{
        checkPassword: "",
        errors: [],
        labelText: {
          labelName: "Nombre",
          labelTel: "Móvil",
          labelCP: "Código Postal",
          labelEmail: "Email",
          labelPass: "Contraseña",
          labelPass2: "Repertir Contraseña"
        },
        msnText: {
          msnString: "Mínim de 6 i màxim de 13 dígits, res més text",
          msnTel: "Sólo dígitos",
          msnCP: "5 dígitos",
          msnEmail: "Formato no correcto",
          msnPass: "De 6 a 13 dígitos que contengan mayúsculas y minúsculas",
          msnPass2: "Las contraseñas no son iguales"
        }

      }
    },
    methods: {
      AddValidation(value){
        return value;
      },
      ControlPass(value){
        return value;
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
    color: red;
}
</style>
