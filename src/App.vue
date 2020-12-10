<template>
  <main id="container">
    <h1 class="title">Diferença entre datas</h1>

    <div class="date_inputs">
      <DateInput
        for_id="datainicial"
        label="Data Inicial" />

      <DateInput
        for_id="datafinal"
        label="Data Final" />
    </div>

    <div class="date_result">
      <input type="text" placeholder="anos; meses; semanas; dias" readonly />
    </div>
  </main>
</template>

<script>
  import DateInput from './components/DateInput';

  export default {
    name: 'App',

    components: {
      DateInput
    }
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
        font-family: 'Quicksand', sans-serif;
      }
    }
  }
</style>
