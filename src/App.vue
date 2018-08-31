<template>
  <div id="app">
    <div class="manager-container">
      <div class="wrapper">
        <!-- <UploadForm /> -->
        <InputForm
          v-bind:inputs='inputs'
          v-bind:errors='errors'
        />
      </div>
    </div>

    <p>{{ inputs.item }}</p>
  </div>
</template>

<script>

// load components here
import InputForm from './components/InputForm.vue'


export default {
  name: 'app',
  components: {
    InputForm
  },
  data(){

    return{
      photos:[],
      inputs:{
        item: '',
        description:'',
        price: '',
      },
      errors:{
        item: '',
        description:'',
        price: '',
      }

    };
  },

}
</script>

<style lang='scss'>
@import './globals/_variables.scss';

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.manager-container{
  margin: auto;
  width: 700px;
  background-color: #fafafa;
  box-shadow: 0px 4px 4px 0px rgba(0, 0, 0, 0.1);

  .wrapper{
    padding: 20px;
  }

}

</style>
