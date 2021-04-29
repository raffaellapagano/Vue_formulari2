<template>
    <div>
        <div class="form-group">
              <label for="nombre">Nombre</label>
              <span v-if="!nombre"> Requerido*</span>
              <input type="text" id="nombre" class="form-control" v-model="nombre" @blur="validarName">
              <div class="error">
              <span class="text-danger" v-if="notAnumber"> Mínim de 6 i màxim de 13 dígits, res més text</span>
              </div>
            </div>
    </div>
</template>

<script>
export default {
  name: 'Name',
  props: {
    msg: String
  },
  data() {
      return{
        nombre: "",
        notAnumber: ""
      }
    },
    methods: {
        validarName: function(){
            if (this.nombre.match(/^[A-Za-z]{6,13}$/)) {
                this.notAnumber = false;
            }else if(this.nombre.match(/[^A-Za-z]/g)) {
                this.notAnumber = true;
            }else{
                this.notAnumber = true;
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