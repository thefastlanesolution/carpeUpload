<template>
  <div class="form-container">
    <form action='#'>
      <div class="column">

        <div class="row form-row">
          <input
            v-model='item'
            :class="{ focused : item }"
            name='item-name'
            type="text">
          <label for='item-name'>Item</label>
        </div>

        <div class="row form-row">
          <textarea
            v-model='description'
            :class="{ focused : description }"
            name='description'
            type="text"></textarea>
          <label for='description'>Description</label>
        </div>

        <div class="row form-row">
          <input
            v-model='price'
            :class="{ focused : price}"
            name='price'
            type='number'>
          <label for='price'>Price</label>
        </div>

        <div class="row form-row">
          <button>Submit</button>
        </div>

      </div>

    </form>

  </div>

</template>

<script>
export default {
  name:'InputForm',
  data:{

    item: '',
    description: '',
    price : '',

  },
  props:{

    // item : String,
    // description: String,
    // price : Number,

  }

}
</script>

<style lang="scss" scoped>

  @import '../globals/_variables.scss';

  .form-row{
    position: relative;
    padding: 15px 0;

    input,textarea{

      &:focus{
        ~label{
          transform: translateY(-20px) scale(.8);
          color: $googleBlue;
        }
      }

      &.focused{
        transform: translateY(-20px) scale(.8);
        color: $googleBlue;
      }

    }

    label{
      pointer-events: none;
      transition: all .2s ease;
      position: absolute;
      transform: translateY(0px) scale(1);
    }

  }


</style>
