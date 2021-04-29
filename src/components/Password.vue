<template>
<div>
        <div class="form-group">
              <label for="contrasena">Contraseña</label>
              <span v-if="!contrasena"> Requerido*</span>
              <input type="password" id="contrasena" class="form-control" v-model="contrasena" @blur="validarPassword">
              <div class="error">
              <span class="text-danger" v-if="pass"> Mínim de 6 i màxim de 13 dígits que contengui majúscules i minúscules.</span>
              </div>
            </div>
            <div class="form-group">
              <label for="contrasena2">Repetir Contraseña</label>
              <span v-if="!contrasena2"> Requerido*</span>
              <input type="password" id="contrasena2" class="form-control" v-model="contrasena2" @blur="validarPassword2">
              <div class="error">
              <span class="text-danger" v-if="pass2"> Las contraseñas no coinciden</span>
              </div>
            </div>
  </div>
</template>

<script>
export default {
  name: 'Password',
  props: {
    msg: String
  },
  data() {
      return{
        correo: "",
        correo2: "",
        pass: "",
        pass2: ""
      }
    },
    methods: {
        validarPassword: function(){
            if(this.contrasena.match(/^(?=.*[a-z])(?=.*[A-Z])[A-Za-z\d$@ñ!%*?&+¿_]{6,13}$/)){
                this.pass = false;
            }else{
                this.pass = true;
            }
        },
        validarPassword2: function () { 
            if(this.contrasena == this.contrasena2){
                this.pass2 = false;
            }else{
                this.pass2 = true;
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