<template>
  <div id="app">
    <div id="types">
      <div class="media-selector"
           v-for='media in mediaTypes'
           :key="media.name"
           :class="{ active : activeType === media.name }"
           @click="activeType = media.name">
        {{ media.name }}
      </div>
    </div>
    <div class="manager-container">
      <div class="wrapper">
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
  created(){
    this.activeType = this.mediaTypes[0].name;
  },
  data(){

    return{
      photos:[],
      activeType: '',
      mediaTypes:[
        {
          name : 'letgo',
          icon : '',
        },
        {
          name : 'facebook',
          icon : '',
        },
      ],
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
  margin: 35px auto 0 auto;
  width: 700px;
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

#types{
  display: flex;

  .media-selector{
    padding: 20px;
    background-color: $backgroundColor;

    &:hover{
      cursor: pointer;
    }

    &:not(.active){
      box-shadow: inset 0px -4px 8px -4px grey;
    }
  }

}

.manager-container{
  background-color: #fafafa;
  box-shadow: 0px 4px 4px 0px rgba(0, 0, 0, 0.1);

  .wrapper{
    padding: 20px;
  }

}

</style>
