<template>
  <div class="manager-container">
    <div class="wrapper">
      <PhotoQueue />
      <UploadForm />
      <InputForm />
    </div>
  </div>
</template>

<script>

import UploadForm from './UploadForm.vue'
import PhotoQueue from './PhotoQueue.vue'
import InputForm from './InputForm.vue'

export default {
  name: 'UploadManager',
  props:{
    property : String

  },
  components: {
    UploadForm,
    PhotoQueue,
    InputForm
  }
}
</script>


<style lang='scss' scoped>

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

