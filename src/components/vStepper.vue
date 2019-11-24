<template>
  <v-stepper v-model="e6" vertical>
    <v-stepper-step :complete="e6 > 1" step="1" editable="editable">
      Configure the manifold
      <!-- <small>Summarize if needed</small> -->
    </v-stepper-step>

    <v-stepper-content step="1">
      <!-- <v-card color="white" class="mb-12" height="200px"> -->
      <v-col cols="12">

        <v-row>
          <v-col cols="3">
            <p class="text-left">Communications Protocol:</p>
          </v-col>
          <v-col cols="4">
            <v-select :items="commProt" dense single-line hide-details hide-selected outlined solo value="EtherNet/IP"></v-select>
          </v-col>
        </v-row>  

        <v-row>
          <v-col cols="3">
            <p class="text-left">Digital Input Modules:</p>
          </v-col>
          <v-col>
            <v-slider v-model="numDin" min="0" max="20" ticks="always"></v-slider>
          </v-col>
          <v-col cols="1">
            <span class="text-right" v-text="numDin"></span>
          </v-col>
        </v-row>  

        <v-row>
          <v-col cols="3">
            <p class="text-left">Digital Output Modules:</p>
          </v-col>
          <v-col>
            <v-slider v-model="numDout" min="0" max="20" ticks="always"></v-slider>
          </v-col>
          <v-col cols="1">
            <span class="text-right" v-text="numDout"></span>
          </v-col>
        </v-row> 


        <v-row>
          <v-col cols="3">
            <p class="text-left">Power Plus Modules:</p>
          </v-col>
          <v-col>
            <v-slider v-model="numPowPlus" min="0" max="20" ticks="always"></v-slider>
          </v-col>
          <v-col cols="1">
            <span class="text-right" v-text="numPowPlus"></span>
          </v-col>
        </v-row> 


        <v-row>
          <v-col cols="3">
            <p class="text-left">Analog 4-20ma Modules:</p>
          </v-col>
          <v-col>
            <v-slider v-model="num4to20" min="0" max="20" ticks="always"></v-slider>
          </v-col>
          <v-col cols="1">
            <span class="text-right" v-text="num4to20"></span>
          </v-col>
        </v-row> 


        <v-row>
          <v-col cols="3">
            <p class="text-left">Analog 0-10v Modules:</p>
          </v-col>
          <v-col>
            <v-slider v-model="num0to10" min="0" max="20" ticks="always"></v-slider>
          </v-col>
          <v-col cols="1">
            <span class="text-right" v-text="num0to10"></span>
          </v-col>
        </v-row> 


        <v-row>
          <v-col cols="3">
            <p class="text-left">Number of Valves:</p>
          </v-col>
          <v-col>
            <v-slider v-model="numValves" min="2" max="32" ticks="always"></v-slider>
          </v-col>
          <v-col cols="1">
            <span class="text-right" v-text="numValves"></span>
          </v-col>
        </v-row> 

        
        <v-radio-group v-model="radios"  mandatory="true">
          <v-radio label="42 Series" value="radio-1" color="primary"></v-radio>
          <v-radio label="92 Series" value="radio-2" color="primary"></v-radio>
        </v-radio-group>
        <!-- </v-card> -->
      </v-col>
      <v-btn color="primary" @click="e6 = 2">Continue</v-btn>
      <v-btn text>Cancel</v-btn>
    </v-stepper-content>

    <v-stepper-step :complete="e6 > 2" step="2" editable="editable">Configure the valves</v-stepper-step>

    <v-stepper-content step="2">
      <v-card color="grey lighten-1" class="mb-12" height="200px"></v-card>
      <v-btn color="primary" @click="e6 = 3">Continue</v-btn>
      <v-btn text>Cancel</v-btn>
    </v-stepper-content>

    <v-stepper-step :complete="e6 > 3" step="3" editable="editable">Select accessories</v-stepper-step>

    <v-stepper-content step="3">
      <v-card color="grey lighten-1" class="mb-12" height="200px"></v-card>
      <v-btn color="primary" @click="e6 = 4">Continue</v-btn>
      <v-btn text>Cancel</v-btn>
    </v-stepper-content>

    <v-stepper-step step="4" editable="editable">View Result</v-stepper-step>
    <v-stepper-content step="4">
      <v-card color="grey lighten-1" class="mb-12" height="200px"></v-card>
      <!-- <v-btn color="primary" @click="e6 = 1">Continue</v-btn> -->
      <!-- <v-btn text>Cancel</v-btn> -->
    </v-stepper-content>
  </v-stepper>
</template>

<script>
export default {
  data() {
    return {
      numDin: 0,
      numDout: 0,
      num4to20: 0,
      num0to10: 0,
      numPowPlus: 0,
      numValves: 2,
      e6: 1,
      //ticks: [0,1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20],
      commProt: ["EtherNet/IP", "EtherCAT", "POWERLINK", "PROFINET", "Modbus/TCP"]
    };
  }
};
</script>