<template>
  <main id="container">
    <h1 class="title">Diferença entre datas</h1>

    <div class="date_inputs">
      <DateInput
        v-model="dateA"
        for_id="datainicial"
        label="Data Inicial" />

      <DateInput
        v-model="dateB"
        for_id="datafinal"
        label="Data Final" />
    </div>

    <div class="date_result">
      <input type="text" placeholder="anos; meses; semanas; dias" :value="dateDifferenceDays" readonly />

      <button :class="{ disabled: !datesFilledProperly }">
        Calcular
      </button>
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
        dateB: '',
        dateDifferenceDays: 0,
        regexp: /(\d{2})\/(\d{2})\/(\d{4})/
      };
    },

    methods: {
      ISO8601Date (date) {
        return date.split('/').reverse().join('/');
      },

      getTimeFromDate (date) {
        const { ISO8601Date } = this;

        return new Date(ISO8601Date(date)).valueOf();
      },
    },

    computed: {
      dayInSeconds () {
        return 1000 * 24 * 3600;
      },

      daysDifference () {
        const { dateTimeA, dateTimeB, dayInSeconds } = this;

        return Math.floor(Math.abs(dateTimeA - dateTimeB) / dayInSeconds);
      },

      dateTimeA () {
        const { dateA, getTimeFromDate } = this;

        return getTimeFromDate(dateA);
      },

      dateTimeB () {
        const { dateB, getTimeFromDate } = this;

        return getTimeFromDate(dateB);
      },

      datesFilledProperly () {
        const { dateA, dateB, regexp } = this;

        return [dateA, dateB].every( date => regexp.test(date) );
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
      },

      datesFilledProperly (current) {
        if (current) {
          const { dateTimeA, dateTimeB, dayInSeconds } = this;

          const dateDiff = Math.floor(Math.abs(dateTimeA - dateTimeB) / dayInSeconds);

          this.dateDifferenceDays = `${dateDiff} dias`;
        } else {
          this.dateDifferenceDays = 'N/A';
        }
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
      height: 70px;
      padding: 5px;
      margin: 10px 0;

      margin-top: 10px;
      flex-direction: column;
      @extend %flex-spacebetween-center;

      input {
        width: 95%;
        color: #fff;
        border: none;
        padding: 4px 0;
        font-size: 10pt;
        text-align: center;
        background: transparent;
        text-transform: uppercase;
        border-bottom: solid 1px #ccc;
        font-family: 'Quicksand', sans-serif;
      }

      button {
        border: none;
        cursor: pointer;
        margin-top: 20px;
        padding: 5px 10px;
        background-color: #fff;
        text-transform: uppercase;
        font-family: 'Nunito', sans-serif;
        box-shadow: 0 2px 5px -2px #000;
        transition: box-shadow .2s ease-in-out;

        &:not(.disabled):active {
          box-shadow: none;
          transform: scale(.98);
        }

        &.disabled {
          opacity: .4;
          cursor: default;
        }
      }
    }
  }
</style>
