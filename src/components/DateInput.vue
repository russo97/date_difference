<template>
  <div class="date_input">
    <input
      required
      type="text"
      :id="for_id"
      inputmode="tel"
      maxlength="10" />
    <label :for="for_id"> {{ label }} </label>
    <div class="active_border"></div>
  </div>
</template>

<script>
export default {
 name: 'DateInput',

 props: {
   for_id: {
     type: String,
     required: true
   },

   label: {
     type: String,
     required: true
   }
 }
}
</script>

<style lang="scss">
  @import '../utils/scss/global.scss';

  .date_inputs {
    width: 100%;
    padding: 5px;

    @extend %flex-spacearound-center;

    .date_input {
      width: 50%;
      height: 25px;
      position: relative;
      @extend %flex-center;

      .active_border {
        width: 80%;
        height: 2px;
        bottom: -2px;
        position: absolute;

        &:after,
        &:before {
          content: '';
          top: 0px;
          width: 0%;
          height: 2px;
          position: absolute;
          transition: .2s ease;
          background-color: #00A6FB;
        }

        &:after  { left: 50%; }
        &:before { right: 50%; }
      }

      label,
      input {
        width: 90%;
        font-size: 12pt;
        text-align: center;
        touch-action: manipulation;
      }

      label {
        cursor: pointer;
        padding: 6px 4px;
        overflow: hidden;
        position: absolute;
        white-space: nowrap;
        text-overflow: ellipsis;
        text-transform: uppercase;
        transition: .2s ease-in-out;
        font-family: 'Quicksand', sans-serif;
      }

      input {
        border: none;
        padding: 4px 4px;
        font-family: 'Nunito', sans-serif;

        &:focus,
        &:valid {
          & ~ label {
            color: #00A6FB;
            font-size: 10pt;
            transform-origin: center bottom;
            transform: translate(0, -20px) scale(.9);
          }

          & ~ .active_border:after,
          & ~ .active_border:before {
            width: 50%;
          }
        }
      }
    }
  }
</style>