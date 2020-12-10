<template>
  <div class="date_input">
    <input type="text" id="dataFinal" inputmode="tel" required />
    <label for="dataFinal">Data final</label>
  </div>
</template>

<script>
export default {
 name: 'DateInput'
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
        font-family: 'Nunito', sans-serif;
      }

      input {
        border: none;
        padding: 4px 4px;
        font-family: 'Nunito', sans-serif;

        &:focus ~ label,
        &:valid ~ label {
          opacity: .7;
          font-size: 10pt;
          transform-origin: center bottom;
          transform: translate(0, -20px) scale(.8);
        }
      }
    }
  }
</style>