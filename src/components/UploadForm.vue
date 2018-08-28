<template>
  <div>
    <form id="photo-drop-zone" class="dropzone" action="#">

    </form>
  </div>

</template>

<script>

import Dropzone from 'dropzone'


const configureDropzone = () => {
    Dropzone.options.myAwesomeDropzone = {
    paramName: "file", // The name that will be used to transfer the file
    maxFilesize: 2, // MB
    accept( file, done ) {

    }
  };
}


export default {
  name: "UploadForm",
  created(){

    configureDropzone();

  },

}
</script>

<style lang="scss" scoped>
  h1{
    color: red;
  }

  #photo-drop-zone{
    border: 3px dashed red;

    &:hover{
      opacity: .6;
      cursor: pointer;

    }

  }

</style>
