<template>
  <main id="container">
    <h1 class="title">Diferença entre datas</h1>

    <div class="date_inputs">
      <div class="date_input">
        <input type="text" inputmode="tel" placeholder="XX/XX/XXXX" />
      </div>

      <div class="date_input">
        <input type="text" inputmode="tel" />
      </div>
    </div>

    <div class="date_result">
      <input type="text" readonly />
    </div>
  </main>
</template>

<script>
  export default {
    name: 'App'
  }
</script>

<style lang="scss">
  main#container {
    width: 90%;
    height: auto;
    padding: 12px 5px;
    max-width: 400px;
    background-color: #fff;
    box-shadow: 0 1px 3px #aaa;

    display: flex;
    align-items: center;
    flex-direction: column;
    justify-content: center;

    h1.title {
      padding: 13px 0;
      font-size: 14pt;
      text-align: center;
      text-transform: uppercase;
      font-family: 'Nunito', sans-serif;
    }

    .date_inputs {
      width: 100%;
      padding: 5px;

      display: flex;
      align-items: center;
      justify-content: space-around;

      .date_input {
        width: 50%;
        height: 25px;

        display: flex;
        align-items: center;
        justify-content: center;

        input {
          width: 90%;
          font-size: 12pt;
          padding: 4px 4px;
          text-align: center;
          border: solid 1px #ccc;
          font-family: 'Nunito', sans-serif;
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
        border: solid 1px #ccc;
      }
    }
  }
</style>
