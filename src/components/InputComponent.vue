<template>
    <div>
        <div class="form-group">
              <label>{{label}}</label>
              <span v-if="!valueInput"> Requerido*</span>
              <input :type="type" 
                     :id="idInput" 
                     class="form-control" 
                     v-model="valueInput" 
                     @blur="ValidationInput">
              <div class="error">
              <span class="text-danger" v-if="!validation"> {{msgInput}}</span>
              </div>
            </div>
    </div>
</template>

<script>
export default {
  name: 'InputComponent',
  props: [
    "label",
    "type",
    "idInput",
    "msgInput",
    "require",
    "errorInput"
  ],
  data() {
      return{
        valueInput: "",
        validation: Boolean,
        message: "",
        checkPassword2: "",
        element:{
          id:this.idInput,
          value: "",
          validation: "",
          msn: this.msgInput
        }
      }
    },
    methods: {
    ValidationInput(){
      
      switch (this.label) {
          case "Nombre": //metodo para validar el Name
            if (this.valueInput.match(/^[A-Za-z]{6,13}$/)) {
                this.validation = true;
                this.element.value = this.valueInput;
            }else if(this.valueInput.match(/[^A-Za-z]/g)) {
                this.validation = false;
            }else if (this.valueInput==""){
                this.validation = "";
            }else{
              this.validation = false;
            }
          break;

          case "Móvil": //metodo para validar el Móvil
            if(this.valueInput.match(/[^0-9]/g)){
                this.validation = false;
                this.element.value = this.valueInput;
            }else if (this.valueInput==""){
                this.validation = "";
            }else{
                this.validation = true;
            }
          break;

          case "Código Postal": //metodo para validar el Código Postal
            if(this.valueInput.match(/[^0-9]/g)){
                this.validation = true;
            }else if(this.valueInput.match(/^[0-9]{5,5}$/gm)){
                this.validation = true;
            }else if(this.valueInput==""){
                this.validation = "";
            }else{
                this.validation = false;
            }
          break;

          case "Email": //metodo para validar el Email
            var texto = this.valueInput;
            var arroba = texto.indexOf("@");
            var punto = texto.indexOf(".");
            if(texto==""){
                this.validation = "";
            }else if (arroba == -1 || punto ==-1){
                this.validation = false;
            }else{
                this.validation = true;
            }
            break;

            case "Contraseña": //metodo para validar el Password
            if(this.valueInput.match(/^(?=.*[a-z])(?=.*[A-Z])[A-Za-z\d$@ñ!%*?&+¿_]{6,13}$/)){
                this.validation = true;
                this.$emit(`Password`, this.valueInput);
            }else{
                this.validation = false;
            }
            break;

            case "Repertir Contraseña": //metodo para validar el Password
            this.validation = "";
            if(this.checkPassword2 === this.valueInput){
                this.validation = true;
            }else{
                this.validation = false;
                alert(this.checkPassword2)
            }
            break;
      
        default:
          break;
      }
    },
    Add(){
      this.element.value = this.valueInput;
      this.$emit(`ReturnValidation`, this.element);
    },
    beforeUpdate(){
        this.$emit(`Password`, this.valueInput);
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
</style>