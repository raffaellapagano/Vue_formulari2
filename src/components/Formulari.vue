<template>
  <div>
    <div class="row">
        <div class="col md-6">
          <h1 class="text-success">Formulario</h1>
          <form @submit.prevent>

            <InputComponent 
              :label="labelText.labelName"
              :type= "'text'"
              :idInput= "'idName'"
              :msgInput="msnText.msnString"
              :require="true"
              @ReturnValidation="AddValidation1"></InputComponent>

              <InputComponent 
              :label="labelText.labelTel"
              :type= "'text'"
              :idInput= "'idTel'"
              :msgInput="msnText.msnTel"
              :require="true"
              @ReturnValidation="AddValidation2"></InputComponent>

              <InputComponent 
              :label="labelText.labelCP"
              :type= "'text'"
              :idInput= "'idCP'"
              :msgInput="msnText.msnCP"
              :require="true"
              @ReturnValidation="AddValidation3"></InputComponent>

              <InputComponent 
              :label="labelText.labelEmail"
              :type= "'email'"
              :idInput= "'idEmail'"
              :msgInput="msnText.msnEmail"
              :require="true"
              @ReturnValidation="AddValidation4"></InputComponent>

              <InputComponent 
              :label="labelText.labelPass"
              :type= "'password'"
              :idInput= "'idPass'"
              :msgInput="msnText.msnPass"
              :require="true"
              @ReturnValidation="AddValidation5"></InputComponent>

              <InputComponent 
              :label="labelText.labelPass2"
              :type= "'password'"
              :idInput= "'idPass2'"
              :msgInput="msnText.msnPass2"
              :require="true"
              :checkPassword2="user.password"
              @ReturnValidation="AddValidation6"></InputComponent>

              
            <hr>
              <div>
            <button type="submit" class="btn btn-primary btn-lg ml-2" @click="AlertValue">Enviar</button>
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
        },
        user: {
          name: "",
          tel: "",
          cP: "",
          email: "",
          password: "",
          password2: ""
        },
        userRegistered: ""
      }
    },
    methods: {
      AddValidation1(value){
        this.user.name = value;
      },
      AddValidation2(value){
        this.user.tel = value;
      },
      AddValidation3(value){
        this.user.cP = value;
      },
      AddValidation4(value){
        this.user.email = value;
      },
      AddValidation5(value){
        this.user.password = value;
      },
      AddValidation6(value){
        this.user.password2 = value;
      },
      AlertValue(){
        this.userRegistered = "";
        let text = `
        Nombre: ${this.user.name}
        Teléfono: ${this.user.tel}
        CP: ${this.user.cP}
        Email: ${this.user.email}
        Password: ${this.user.password}`

        if(this.user.name && this.user.tel && this.user.cP && this.user.email && this.user.password && this.user.password2){
            alert(text);

            this.user.name = "";
            this.user.tel = "";
            this.user.cP = "";
            this.user.email = "";
            this.user.password = "";
            this.user.password2 = "";
      }else{
            alert("Datos incorrectos");
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
    color: red;
}
</style>
