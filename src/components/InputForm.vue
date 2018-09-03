<template>
  <div class="form-container">

    <form id="photo-drop-zone" @click.stop class='dropzone' action='#' >
      <!-- Dropzone -->
      <h2 class='dz-message'>Drop files <span>here</span> or click to upload</h2>
      <div id='preview' class="dropzone-previews"></div>

      <!-- Form Inputs -->
      <div @click.prevent.stop class="column">

        <div class="row form-row">
          <input
            v-model='inputs.item'
            :class="{ focused : inputs.item }"
            name='item-name'
            type="text">
          <label for='item-name'>Item</label>
          <div class="error"> {{ errors.item }}</div>
        </div>

        <div class="row form-row">
          <textarea
            v-model='inputs.description'
            :class="{ focused : inputs.description }"
            name='description'
            type="text">
            </textarea>
          <label for='description'>Description</label>
          <div class="error">{{ errors.description }}</div>
        </div>

        <div class="row form-row">
          <input
            v-model='inputs.price'
            :class="{ focused : inputs.price }"
            name='price'
            type='number'>
          <label for='price'>Price</label>
          <div class="error">{{ errors.price }}</div>
        </div>

      <!-- Submit -->
        <div class="row form-row">
          <button id="submit">Submit</button>
        </div>

      </div>

    </form>

  </div>

</template>

<script>
  import Dropzone from 'dropzone'

  const previewTemplate = '<div id="tpl" style="margin:10px;">\
                              <div class="dz-preview dz-file-preview">\
                                <div class="dz-details">\
                                  <div class="dz-filename"><span data-dz-name></span></div>\
                                  <div class="dz-size" data-dz-size></div>\
                                  <img data-dz-thumbnail />\
                                </div>\
                                <div class="dz-progress"><span class="dz-upload" data-dz-uploadprogress></span></div>\
                                <div class="dz-error-message"><span data-dz-errormessage></span></div>\
                              </div>';

  const configureDropzone = () => {
      Dropzone.options.photoDropZone = {
      paramName: "file",     						// The name that will be used to transfer the file
      previewsContainer : '#preview',		// HTML Element to contain the image thumbnails
      previewTemplate,       						// custom template to display image thumbnail
      maxFilesize: 2,        						// MB
      addRemoveLinks : true, 						// provides option to remove file (or cancel if already uploading)
      autoProcessQueue: false, 					// Dropzone should wait for the user to click a button to upload
      uploadMultiple: true, 						// Dropzone should upload all files at once (including the form data) not all files individually
      parallelUploads: 100, 						// that means that they shouldn't be split up in chunks as well
      maxFiles: 100, 										// this is to make sure that the user doesn't drop more files than allowed in one request.
      init(){

        const self = this;

        this.element
          .querySelector('#submit')
          .addEventListener( 'click', event => {
          event.preventDefault();
          event.stopPropagation();
          self.processQueue();
        } );

        this.on("sendingmultiple", ( event ) => {

          console.log( event );
          // Gets triggered when the form is actually being sent.
          // Hide the success button or the complete form.
        } );
        this.on("successmultiple", ( files, result ) => {
          // Gets triggered when the files have successfully been sent.
          // Redirect user or notify of success.
        } );
        this.on("errormultiple", ( files, result ) => {
          // console.error( result );
          // Gets triggered when there was an error sending the files.
          // Maybe show form again, and notify user of error
        } );

      }

    };
  }

  export default {
    name:'InputForm',
    mounted(){
      this.dropZone = configureDropzone();
    },
    props:{
      inputs : Object,
      errors : Object,
      type   : String
    },

    computed : {
      files(){
        return this.dropZone.files;
      }
    },
    data(){
      return{
        dropZone : null,
      }
    },

  }
</script>

<style lang="scss" scoped>
  @import '../globals/_variables.scss';

  a.dz-remove{
    text-decoration: none;
  }

  .dz-message{
    cursor: pointer;
    span{
      color: red;
    }
  }

  // dropzone styling
	#photo-drop-zone{
    max-height: 750px;

		#preview{
      display: flex;
      flex-wrap: wrap;
      padding: 10px;
      justify-content: center;

      &.populated{
        border: 1px solid blue;
      }

		}
	}

  // input styling
  form{
    .column{
      margin: 0 auto;
      width: 350px;
    }
  }

  .form-row{
    position: relative;
    padding: 15px 0;

    input,textarea{
      width: 100%;
      min-height: 30px;

      &:focus{
        ~label{
          transform: translateY(-20px) scale(.8);
          color: $googleBlue;
        }
      }

      &.focused{

       ~label{
          transform: translateY(-20px) scale(.8);
          color: $googleBlue;
        }
      }

    }

    label{
      pointer-events: none;
      transition: all .2s ease;
      position: absolute;
      transform: translate(5px, 5px) scale(1)
    }

    button{
      margin: 0 auto;
      width: 125px;
      height: 30px;
      border-radius: 5px;
      outline: none;
    }

  }

</style>
