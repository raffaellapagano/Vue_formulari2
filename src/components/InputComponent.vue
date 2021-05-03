<template>
    <div>
        <div class="form-group">
              <label>{{nameInput}}</label>
              <span v-if="!valueInput"> Requerido*</span>
              <input type="type" id="idInput" class="form-control" v-model="valueInput" @blur="ValidarName">
              <div class="error">
              <span class="text-danger" v-if="errorInput"> {{msgInput}}</span>
              </div>
            </div>
    </div>
</template>

<script>
export default {
  name: 'Name',
  props: {
    nameInput: String,
    type: String,
    idInput: String,
    valueInput: String,
    errorInput: Boolean,
    msgInput: String
  },
  data() {
      return{
        nombre: "",
        notAnumber: ""
      }
    },
    methods: {
        ValidarName(){
          this.errorInput = "";
            if (this.valueImput.match(/^[A-Za-z]{6,13}$/)) {
                this.errorInput = false;
            }else if(this.valueImput.match(/[^A-Za-z]/g)) {
                this.errorInput = true;
            }else if (this.valueImput==""){
                this.errorInput = "";
            }else{
              this.errorInput = true;
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
</style>