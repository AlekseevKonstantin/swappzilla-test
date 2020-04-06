<template>
  <v-dialog v-model="dialog" width="790" style="box-shadow: none !important;">
    <v-card class="acc-v-card">
      <v-btn icon 
            color="label"
            class="acc-dialog-close"
            @click="changeState">
        <v-icon>mdi-close</v-icon>
      </v-btn>
      <v-container class="py-0">
        <v-row justify="space-between">
          <v-col cols="auto pa-0">
            <v-tabs v-model="tab" color="dark" class="acc-tabs">
              <v-tab v-for="(tab, i) in tabs"
                      :class="[{'mr-10': i !== tabs.length-1 }, 'title pa-0 acc-tab']"
                      :key="i" 
                      style="text-transform: none;">{{tab}}</v-tab>
            </v-tabs>
          </v-col>

         
        </v-row>

        <v-row class="mt-10 justify-center">
          <v-form v-model="valid" class="acc-form">
            <v-tabs-items v-model="tab">
              <v-tab-item transition="fade-transition" 
                          reverse-transition="fade-transition">
                
                <v-select :items="items" 
                          flat
                          height="50"
                          class="mb-5 acc-v-input"
                          append-icon="mdi-chevron-down"
                          background-color="border" 
                          label="Choose exchange" 
                          color="label"
                          hide-details="true"
                          solo>
                  <template v-slot:append>
                    <v-icon color="label">mdi-chevron-down</v-icon>
                  </template>
                </v-select>

                <v-select :items="items" 
                          flat
                          height="50"
                          class="acc-v-input"
                          append-icon="mdi-chevron-down"
                          background-color="border" 
                          label="Choose currency" 
                          color="label"
                          hide-details="true"
                          solo>
                  <template v-slot:append>
                    <v-icon color="label">mdi-chevron-down</v-icon>
                  </template>
                </v-select>

                <div class="acc-qr">
                  <img :src="require(`./../assets/qr.png`)" alt="">
                </div>

                <v-card-text class="acc-card-text">FGBfvcnkfdnvkk74365832ybvcvdfvfvb</v-card-text>

                <v-btn color="primary" 
                        block 
                        height="50" 
                        class="acc-v-btn"
                        style="text-transform: none;">
                        Copy
                </v-btn>

              </v-tab-item>

              <v-tab-item transition="fade-transition" 
                          reverse-transition="fade-transition">
                <v-select :items="items" 
                          flat
                          height="50"
                          class="mb-5 acc-v-input"
                          append-icon="mdi-chevron-down"
                          background-color="border" 
                          label="Choose exchange" 
                          color="label"
                          hide-details="true"
                          solo>
                  <template v-slot:append>
                    <v-icon color="label">mdi-chevron-down</v-icon>
                  </template>
                </v-select>

                <v-select :items="items" 
                          flat
                          height="50"
                          class="mb-5 acc-v-input"
                          append-icon="mdi-chevron-down"
                          background-color="border" 
                          label="Choose currency" 
                          color="label"
                          hide-details="true"
                          solo>
                
                  <template v-slot:append>
                    <v-icon color="label">mdi-chevron-down</v-icon>
                  </template>
                </v-select>  

                <v-select :items="items" 
                          flat
                          height="50"
                          class="mb-5 acc-v-input"
                          append-icon="mdi-chevron-down"
                          background-color="border" 
                          label="Withdraw amount" 
                          color="label"
                          hide-details="true"
                          solo>
                
                  <template v-slot:append>
                    <div class="text-label once">
                      <span>Max</span>
                    </div>
                  </template>
                </v-select>  

                <v-btn color="primary" 
                      block 
                      height="50" 
                      class="acc-v-btn"
                      style="text-transform: none;">
                      Withdraw
                </v-btn>

              </v-tab-item>
              <v-tab-item transition="fade-transition" 
                          reverse-transition="fade-transition">
                
                <div>
                  <span class="acc-label">From</span>
                  <v-select :items="items" 
                            flat
                            height="50"
                            class="mb-5 acc-v-input"
                            append-icon="mdi-chevron-down"
                            background-color="border" 
                            label="Choose exchange" 
                            color="label"
                            hide-details="true"
                            solo>
                    <template v-slot:append>
                      <v-icon color="label">mdi-chevron-down</v-icon>
                    </template>
                  </v-select>
                </div>

                <div>
                  <span class="acc-label">To</span>
                  <v-select v-for="item in ['to1','to2']"
                            :key="item"
                            :items="items" 
                            flat
                            height="50"
                            class="mb-5 acc-v-input"
                            append-icon="mdi-chevron-down"
                            background-color="border" 
                            label="Choose exchange" 
                            color="label"
                            hide-details="true"
                            solo>
                    <template v-slot:append>
                      <v-icon color="label">mdi-chevron-down</v-icon>
                    </template>
                  </v-select>

                  <div class="acc-text-field-menu">
                    
                    <v-text-field class="acc-v-textfield" 
                                flat 
                                single-line 
                                solo
                                outlined
                                background-color="border" 
                                hide-details="true"
                                @click="isAccMenu = !isAccMenu">
                    </v-text-field> 

                    <SlideToggle>
                      <div v-if="isAccMenu" class="acc-wrap">
                        <v-card class="acc-text-field-card">
                          <div class="d-flex" >
                            <span class="text-label balance">
                              Balance: <span id="balance">0.04763864</span>
                            </span>
                          </div>
                          <div class="d-flex flex-wrap" style="margin-bottom: -10px;">
                            <span v-for="(label, i) in textLabels" class="text-label" :key="i">{{label}}</span> 
                          </div>
                        </v-card>  
                      </div>
                    </SlideToggle>
                  </div> 
                                
                </div>
              </v-tab-item>

            </v-tabs-items>
          </v-form>
        </v-row>
      </v-container>
    </v-card>
  </v-dialog>
</template>

<script>
  import SlideToggle from './slideToggle'

  
  export default {
    model: {
      prop: 'activator',
      event: 'changestate',
    },
    props: {
      activator: {
        type: Boolean,
        default: false
      }
    },
    name: 'FundYourAcc',
    data: () => ({
      tab: null,
      isClose: false,
      valid: false,
      showMenu: false,
      isAccMenu: false,
      tabs: ['Deposit', 'Withdraw', 'Rebalance'],
      items: ['1', '2', '3', '4'],
      textLabels: ['10%', '20%', '50%', '100%', 'Split']
    }),
    
    components: {
      SlideToggle
    },

    computed: {
      dialog() {
        return this.activator
      }
    },
    methods: {
      changeState(){
        this.$emit ('changestate', false)
      }
    }
  }
</script>

<style>

  .acc-tabs .v-tabs-slider-wrapper {
    height: 4px !important;
  }

  .acc-v-card {
    position: relative;
    box-shadow: none !important;
    padding: 32px 40px 70px 40px;  
  }

  .acc-form {
    max-width: 380px; 
    width: 100%;
  }

  .acc-dialog-close {
    position: absolute !important;
    top: 22px;
    right: 22px;
    width: 33px !important;
    height: 33px !important;
  }

  .acc-dialog-close .v-icon {
    font-size: 33px !important;
    width: 33px !important;
    height: 33px !important;
  }

  .acc-v-input,
  .acc-v-list-item,
  .acc-v-btn {
    font-family: 'Open Sans', sans-serif !important;
  }

  .acc-v-input {
    width: 100%;
  }

  .acc-v-input .v-select__selection {
    font-family: 'Open Sans', sans-serif;
    font-weight: normal;
    font-size: 14px;
    line-height: 14px;
    color: #3C484C;
  }

  .acc-v-textfield {
    height: 50px !important;
    font-family: 'Open Sans', sans-serif !important;
    font-weight: normal;
    font-size: 14px;
    line-height: 14px;
    color: #3C484C;
  }

  .acc-v-textfield fieldset {
    border: 1px solid transparent !important; 
    transition: border-color .3s ease-in-out !important;
  }

  .acc-v-textfield .v-input__control,
  .acc-v-textfield .v-text-field__slot,
  .acc-v-textfield .v-input__slot {
    height: 50px !important;
    min-height: 0 !important;
  }

  .acc-v-textfield.v-input--is-focused fieldset {
    border: 1px solid  #54B2C8 !important;
  }
  
  .v-application .v-tabs .acc-tab {
    font-family: 'Open Sans', sans-serif !important;
    line-height: 27px;
    height: 27px;
    min-width: 40px !important;
  }

  .acc-v-btn {
    font-weight: bold;
    font-size: 14px;
  }

  .acc-qr {
    width: 119px;
    height: 112px;
    margin: 37px auto 27px auto;
  }

  .acc-card-text {
    font-family: 'Open Sans', sans-serif;
    font-size: 16px;
    line-height: 22px;
    text-align: center;
    color: #3C484C;
    padding: 0 !important;
    margin: 0 auto 29px auto;
  }

  .acc-label {
    display: inline-block;
    font-family: 'Open Sans', sans-serif;
    font-weight: normal;
    font-size: 12px;
    line-height: 16px;
    color: #3C484C;
    margin-bottom: 10px;
    margin-left: 15px;
  }

  .acc-text-field-card {
    background: #FFFFFF;
    border: 1px solid #F0F0F0;
    box-sizing: border-box;
    box-shadow: 0px 6px 6px rgba(60, 72, 76, 0.06) !important;
    padding: 20px !important;
  }

  .text-label {
    background: #C4C4C4;
    border-radius: 5px;
    font-family: 'Open Sans', sans-serif;
    font-style: normal;
    font-weight: bold;
    font-size: 12px;
    line-height: 16px;
    color: #FFFFFF;
    padding: 8px 10px;
    margin-right: 10px;
    margin-bottom: 10px;
  }

  .text-label.once {
    margin: 0;
  }

  .text-label.balance {
    color: #2A6591;
    background: rgba(42, 101, 145, 0.1);
  }

  .text-label.balance:hover {
    cursor: default;
  }

  .text-label:hover {
    cursor: pointer;
  }

  @media (max-width: 600px) {
    .v-application .v-tabs .acc-tab {
      font-size: 12px !important;
      margin-right: 20px !important;
    }

    .acc-v-card {
      padding: 15px;  
    }

    .acc-form {
      margin-left: 0;
    }

    .v-dialog {
      margin-left: 10px !important;
      margin-right: 10px !important;
    }

    .v-slide-group__prev {
      display: none !important;
    }

    .acc-dialog-close {
      margin-top: 0px;
      width: 16px !important;
      height: 16px !important;
    }

    .acc-dialog-close .v-icon {
      font-size: 24px !important;
      width: 16px !important;
      height: 16px !important;
    }
  }
</style>


