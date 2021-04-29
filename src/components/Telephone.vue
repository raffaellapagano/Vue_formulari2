<template>
    <div>
        <div class="form-group">
              <label for="telephone">Telephone</label>
              <span v-if="!telephone"> Requerido*</span>
              <input type="text" id="telephone" class="form-control" v-model="telephone" @blur="validarTel">
              <div class="error">
              <span class="text-danger" v-if="isAnumber"> Res més números</span>
              </div>
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
        telephone: "",
        isAnumber: ""
      }
    },
    methods: {
        validarTel: function(){
            if(this.telephone.match(/[^0-9]/g)){
                this.isAnumber = true;
            }else{
                this.isAnumber = false;
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