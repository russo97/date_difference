<template>
  <div class="date_input">
    <input
      required
      type="text"
      :id="for_id"
      maxlength="10"
      inputmode="tel"
      @input="changeDate" />

    <label :for="for_id">
      {{ label }}
    </label>

    <div class="active_border" :class="{ error: !dataFilledProperly }"></div>
  </div>
</template>

<script>
  export default {
    name: 'DateInput',

    data () {
      return {
        currentDate: ''
      };
    },

    methods: {
      changeDate ($event) {
        this.currentDate = $event.target.value;
      }
    },

    computed: {
      dataFilledProperly () {
        const { currentDate } = this;

        return currentDate.length && /(\d{2})\/(\d{2})\/(\d{4})/.test(currentDate);
      }
    },

    props: {
      for_id: {
        type: String,
        required: true
      },

      label: {
        type: String,
        required: true
      }
    },

    watch: {
      dataFilledProperly (current) {
        if (current) {
          this.$emit('input', this.currentDate);
        }
      }
    }
  }
</script>

<style lang="scss">
  @import '../utils/scss/global.scss';

  .date_input {
    width: 50%;
    height: 25px;
    position: relative;
    @extend %flex-center;

    @media (max-width: 320px) {
      width: 90%;
      height: 35px;
    }

    .active_border {
      width: 80%;
      height: 2px;
      bottom: -2px;
      position: absolute;

      &.error:after,
      &.error:before {
        background: red;        
      }

      &:after,
      &:before {
        content: '';
        top: 0px;
        width: 0%;
        height: 2px;
        position: absolute;
        transition: .2s ease;
        background-color: #fff;
      }

      &:after  { left: 50%; }
      &:before { right: 50%; }
    }

    label,
    input {
      color: #fff;
      width: 90%;
      font-size: 12pt;
      text-align: center;
      background: transparent;
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
          opacity: .6;
          transform-origin: center bottom;
          transform: translate(0, -25px) scale(.6);
        }

        & ~ .active_border:after,
        & ~ .active_border:before {
          width: 50%;
        }
      }
    }
  }
</style>
