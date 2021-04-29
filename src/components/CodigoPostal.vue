<template>
    <div>
        <div class="form-group">
              <label for="cp">CP</label>
              <span v-if="!cp"> Requerido*</span>
              <input type="text" id="cp" class="form-control" v-model="cp" @blur="validarCP">
              <div class="error">
              <span class="text-danger" v-if="cpControl"> Res més números</span>
              </div>
            </div>
    </div>
</template>

<script>
export default {
  name: 'CodigoPostal',
  props: {
    msg: String
  },
  data() {
      return{
        cp: "",
        cpControl: ""
      }
    },
    methods: {
        validarCP: function () {  
            if(this.cp.match(/[^0-9]/g)){
                this.cpControl = false;
            }else if(this.cp.match(/^[0-9]{5,5}$/gm)){
                this.cpControl = false;
            }else{
                this.cpControl = true;
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