<template>
  <v-container>
    <v-row class="text-center">
      <v-col cols="12">
        <v-img
          :src="require('../assets/logo.svg')"
          class="my-3"
          contain
          height="200"
        />
      </v-col>

      <v-col class="mb-4">
        <h1 class="display-2 font-weight-bold mb-3">
          Welcome to Vuetify
        </h1>
      </v-col>
      <v-col class="col-12">
        <v-btn
            color="primary"
            elevation="2"
            large
            @click="overlay = true"
        >
          <span class="mr-2">open modal</span>
        </v-btn>
        <v-overlay
            :value="overlay"
            color="gray"
            :dark="false"
            :opacity="1"
        >
          <v-card
              min-width="780"
          >
            <v-card-actions class="pb-7 pt-4 px-8">
              <v-tabs v-model="active_tab">
                <v-tabs-slider color="dark"></v-tabs-slider>
                <v-tab
                    v-for="(item, index) in list"
                    :key="index"
                    :class="[
                      'text-none',
                      'font-weight-regular',
                      'title',
                      'pa-0',
                      'mx-2',
                      {'label--text': active_tab !== index},
                      {'dark--text': active_tab === index},
                      'tab-'+index
                    ]"
                >
                  {{ item }}
                </v-tab>
              </v-tabs>

              <v-icon
                  @click="overlay=!overlay"
              >
                mdi-close
              </v-icon>

            </v-card-actions>
            <v-container  class="d-flex justify-center pb-16">
              <v-col md=6 class="pa-0 pb-5">

                <v-autocomplete
                  filled
                  solo-inverted
                  color="border"
                  label="Choose exchange"
                  append-icon="mdi-chevron-down"
                  :dark="false"
              ></v-autocomplete>


                <v-autocomplete
                    filled
                    solo-inverted
                    color="border"
                    label="Choose currency"
                    append-icon="mdi-chevron-down"
                ></v-autocomplete>


                <v-text-field
                    filled
                    solo-inverted
                    color="border"
                    label="Withdraw amount"
                >
                  <template slot="append">
                    <v-btn
                        color="label"
                        class="px-0 white--text text-none max-button"
                        small
                    >
                      Max
                    </v-btn>
                  </template>
                </v-text-field>


                <v-btn
                  block
                  color="primary"
                  elevation="2"
                  large
                  @click="overlay = true"
                  grow
                  height="50"
                >
                  <span class="mr-2 text-none font-weight-bold">Withdraw</span>
                </v-btn>

              </v-col>
            </v-container>
          </v-card>
        </v-overlay>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
  export default {
    name: 'HelloWorld',
    data: () => ({
      overlay: false,
      active_tab: 1,
      list: ['Deposit', 'Withdraw', 'Rebalance']
    }),
  }
</script>
<style>
.v-application,
.v-application .title {
  font-family: 'OpenSans', sans-serif !important;
  font-style: normal!important;
}
.v-tabs-slider-wrapper {
  height: 4px!important;
}
.v-application .mx-2.tab-0 {
  margin-left: 0!important;
}
.v-text-field.v-text-field--solo:not(.v-text-field--solo-flat) > .v-input__control > .v-input__slot {
  box-shadow: none !important;
}

.max-button {
  min-width: 48px!important;
  height: 32px!important;
}
</style>
