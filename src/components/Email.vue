<template>
        <div class="form-group">
              <label for="email">Email</label>
              <span v-if="!correo"> Requerido*</span>
              <input type="email" id="email" class="form-control" v-model="correo" @blur="validarEmail">
              <div class="error">
              <span class="text-danger" v-if="alto"> Email no valid</span>
              </div>
        </div>
</template>

<script>
export default {
  name: 'Telephone',
  props: {
    msg: String
  },
  data() {
      return{
        correo: "",
        alto: ""
      }
    },
    methods: {
        validarEmail: function(){
            var texto = this.correo;
            var arroba = texto.indexOf("@");
            var punto = texto.indexOf(".");
            if (arroba == -1 || punto ==-1){
                this.alto = true;
            }else{
                this.alto = false;
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