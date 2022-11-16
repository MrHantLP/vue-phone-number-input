<template>
  <div
    id="app"
    :class="{ 'dark': dark }"
  >
    <h1 class="text-center py-3">
      VuePhoneNumberInput
    </h1>
    <div class="component mb-2 w-2/3">
      <VuePhoneNumberInput
        id="phoneNumber1"
        v-model="phoneNumber"
        color="#00CBFF"
        valid-color="#00CBFF"
        fetch-country
        no-flags
        show-code-on-list
        class="mb-2"
        enable-code-search
        @update="onUpdate"
      />
      <b>v-model</b> : {{ phoneNumber }}
    </div>
  </div>
</template>

<script>
  import VuePhoneNumberInput from './VuePhoneNumberInput'

  export default {
    name: 'App',
    components: {
      VuePhoneNumberInput
    },
    data() {
      return {
        phoneNumber: null,
        phoneNumber2: null,
        phoneNumber3: '0665656565',
        defaultCountry: 'FR',
        countriesList: ['FR', 'BE', 'DE'],
        countriesIgnored: ['AF', 'AD', 'AL'],
        translations: {
          countrySelectorLabel: 'Code pays',
          countrySelectorError: 'Choisir un pays',
          phoneNumberLabel: 'Numéro de téléphone',
          example: 'Exemple :'
        },
        results: {},
        results2: {},
        results3: {},
        dark: false,
        disabled: false,
        hasLoaderActive: false,
        hasErrorActive: false
      }
    },
    computed: {
      resultsTable () {
        return Object.keys(this.results)
      },
      resultsTable2 () {
        return Object.keys(this.results2)
      },
      resultsTable3 () {
        return Object.keys(this.results3)
      }
    },
    methods: {
      onUpdate (payload) {
        this.results = payload
      },
      onUpdate2 (payload) {
        this.results2 = payload
      },
      onUpdate3 (payload) {
        this.results3 = payload
      }
    }
  }
</script>

<style lang="scss">
html,
body {
  padding: 0;
  margin: 0;
}
</style>

<style lang="scss" scoped>
@import '@/assets/scss/variables';
@import 'style-helpers';

#app {
  font-family: 'Roboto', 'Avenir', Helvetica, Arial, sans-serif;
  color: $text-color;
  height: 100%;
  min-height: 100%;
  padding: 1px;
  margin: 0;
  font-size: 14px;

  &.dark {
    background-color: $bg-color-dark;

    h1 {
      color: rgba(255, 255, 255, 0.7);
    }

    header {
      color: rgba(255, 255, 255, 0.7);
    }
  }
}

h1,
h2,
h3,
h4,
h5,
h6 {
  color: dodgerblue;
}

hr {
  border: 0;
  border-top: 1px solid #EBEBEB;
}

*,
*::before,
*::after {
  box-sizing: border-box;
}

.component {
  padding: 10px;
  background: #FFF;
  border-radius: 4px;
  border: 1px solid #EBEBEB;

  &:hover {
    box-shadow:
      0 0 8px 0 rgba(232, 237, 250, 0.6),
      0 2px 4px 0 rgba(232, 237, 250, 0.5);
  }

  &.options {
    margin-bottom: 20px;
  }
}

.component-container {
  margin: 0 10px 20px 10px;
  padding: 20px;
  background: #FFF;
  border-radius: 4px;
  border: 1px solid #EBEBEB;
  min-width: 300px;
  transition: all 0.25s cubic-bezier(0.645, 0.045, 0.355, 1);
  flex: 1 0 48%;

  &:hover {
    box-shadow:
      0 0 8px 0 rgba(232, 237, 250, 0.6),
      0 2px 4px 0 rgba(232, 237, 250, 0.5);
  }

  &.dark {
    background-color: $bg-color-dark;
    color: #FFF;

    textarea {
      background: $bg-color-dark;
      color: dodgerblue;
    }
  }
}

table {
  border-spacing: 0;
  border-collapse: collapse;
  display: block;
  overflow: auto;
  margin-top: 0;
  margin-bottom: 16px;

  tr {
    background-color: #FFF;
    border-top: 1px solid #C6CBD1;

    th,
    td {
      padding: 6px 13px;
      border: 1px solid #DFE2E5;
    }

    &:nth-child(2n) {
      background-color: #F6F8FA;
    }
  }
}

.dark {
  .component-container,
  .component {
    border: 1px solid $hover-color-dark;
    background-color: $bg-color-dark;

    &:hover {
      box-shadow: 0 0 8px 0 rgba(0, 0, 0, 0.6), 0 2px 4px 0 rgba(0, 0, 0, 0.5);
    }

    color: rgba(255, 255, 255, 0.7);
  }

  hr {
    border-color: $hover-color-dark;
  }

  .btn {
    &:hover {
      box-shadow: 0 0 8px 0 rgba(0, 0, 0, 0.6), 0 2px 4px 0 rgba(0, 0, 0, 0.5) !important;
    }
  }

  table tr {
    background-color: $hover-color-dark;
    border-top: 1px solid $hover-color-dark;

    th,
    td {
      border: 1px solid $hover-color-dark;
    }

    &:nth-child(2n) {
      background-color: $bg-color-dark;
    }
  }
}

@media screen and (max-width: 1024px) {
  .components-container.flex {
    flex-direction: column;
  }
}
</style>
