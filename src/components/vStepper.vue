<template>
  <v-stepper v-model="e6" vertical>
    <v-stepper-step :complete="e6 > 1" step="1" editable="editable">
      Configure the manifold
      <!-- <small>Summarize if needed</small> -->
    </v-stepper-step>

    <v-stepper-content step="1">
      <!-- <v-card color="white" class="mb-12" height="200px"> -->
      <v-col cols="8">
        <v-combobox v-model="select" :commProt="commProt" label="Select the communications protocol"></v-combobox>
        <v-slider
          v-model="numDin"
          label="Number of Digital Input Modules"
          min="0"
          max="20"
        >
          <template v-slot:append>
            <span v-text="numDin"></span>
          </template>
        </v-slider>
        <v-slider v-model="numDout" label="Number of Digital Output Modules" min="0" max="20">
          <template v-slot:append>
            <span v-text="numDout"></span>
          </template>
        </v-slider>
        <v-slider v-model="num4to20" label="Number of Analog 4-20ma Modules" min="0" max="20">
          <template v-slot:append>
            <span v-text="num4to20"></span>
          </template>
        </v-slider>
        <v-slider v-model="num0to10" label="Number of Analog 0-10v Modules" min="0" max="20">
          <template v-slot:append>
            <span v-text="num0to10"></span>
          </template>
        </v-slider>
        <v-slider v-model="numPowPlus" label="Number of Power Plus Modules" min="0" max="20">
          <template v-slot:append>
            <span v-text="numPowPlus"></span>
          </template>
        </v-slider>
        <v-slider v-model="numValves" label="Number of Valves" value="2" min="2" max="20">
          <template v-slot:append>
            <span v-text="numValves"></span>
          </template>
        </v-slider>
        
        <v-radio-group v-model="radios" row :mandatory="true">
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
      commProt: ["EtherNet/IP", "EtherCAT", "POWERLINK", "PROFINET", "Modbus/TCP"]
    };
  }
};
</script>