<template>
  <main id="container">
    <h1 class="title">Diferença entre datas</h1>

    <div class="date_inputs">
      <div class="date_input">
        <input type="text" id="dataInicial" inputmode="tel" required />
        <label for="dataInicial">Data inicial</label>
      </div>

      <div class="date_input">
        <input type="text" id="dataFinal" inputmode="tel" required />
        <label for="dataFinal">Data final</label>
      </div>
    </div>

    <div class="date_result">
      <input type="text" placeholder="anos; meses; semanas; dias" readonly />
    </div>
  </main>
</template>

<script>
  export default {
    name: 'App'
  }
</script>

<style lang="scss">
  @import './utils/scss/global.scss';

  main#container {
    width: 90%;
    height: auto;
    max-width: 400px;
    padding: 12px 5px;
    background-color: #fff;
    box-shadow: 0 1px 3px #aaa;

    @extend %flex-center;
    flex-direction: column;
    @include border-radius(3px);

    h1.title {
      color: #444;
      padding: 13px 0;
      font-size: 14pt;
      text-align: center;
      margin-bottom: 10px;
      text-transform: uppercase;
      font-family: 'Nunito', sans-serif;
    }

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

    .date_result {
      width: 100%;
      height: 35px;
      padding: 5px;

      display: flex;
      margin-top: 10px;
      align-items: center;
      justify-content: center;

      input {
        width: 95%;
        padding: 4px 0;
        font-size: 10pt;
        text-align: center;
        border: solid 1px #ccc;
        text-transform: uppercase;
        font-family: 'Nunito', sans-serif;
      }
    }
  }
</style>
