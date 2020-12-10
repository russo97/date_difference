<template>
  <main id="container">
    <h1 class="title">Diferença entre datas</h1>

    <div class="date_inputs">
      <DateInput
        v-model="dateA"
        for_id="datainicial"
        label="Data Inicial" />

      <DateInput
        :value="dateB"
        v-model="dateB"
        for_id="datafinal"
        label="Data Final" />
    </div>

    <div class="date_result">
      <input type="text" placeholder="anos; meses; semanas; dias" :value="isNaN(dateTimeA)" readonly />
    </div>
  </main>
</template>

<script>
  import DateInput from './components/DateInput';

  export default {
    name: 'App',

    data () {
      return {
        dateA: '',
        dateB: ''
      };
    },

    methods: {
      ISO8601Date (date) {
        return date.split('/').reverse().join('/');
      },

      getTimeFromDate (date) {
        return new Date(date).valueOf();
      }
    },

    computed: {
      dateTimeA () {
        const { dateA, getTimeFromDate, ISO8601Date } = this;

        return getTimeFromDate(ISO8601Date(dateA));
      },

      dateTimeB () {
        const { dateB, getTimeFromDate, ISO8601Date } = this;

        return getTimeFromDate(ISO8601Date(dateB));
      }
    },

    components: {
      DateInput
    },

    watch: {
      dateA (current) {
        console.log('dataA', current);
      },

      dateB (current) {
        console.log('dataB', current);
      }
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
    background-color: #14273d;
    box-shadow: 0 10px 50px -10px #222;

    @extend %flex-center;
    flex-direction: column;
    @include border-radius(3px);

    h1.title {
      color: #4475e2;
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

      @media (max-width: 320px) {
        height: 120px;
        flex-direction: column;
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
        background: transparent;
        border: solid 1px #ccc;
        text-transform: uppercase;
        font-family: 'Quicksand', sans-serif;
      }
    }
  }
</style>
