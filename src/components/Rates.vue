<template>
  <v-app>
    <div>
      <v-app-bar color="deep-purple accent-4" dense dark>
        <v-toolbar-title>RateMon UI</v-toolbar-title>
        <v-spacer></v-spacer>
        <div>
          <v-btn color="white" text x-large @click.stop="dialog = true">
            {{ selectedTriggers.length}} Triggers
          </v-btn>
          &nbsp;RUN:

          <v-btn color="white" text >
            
          <v-autocomplete
        v-model="selectedRun"
        small
        :items="availableRuns"
      ></v-autocomplete></v-btn>
        </div>
        <v-menu left bottom>
        </v-menu>
      </v-app-bar>
    </div>
    <v-content>
      <v-container>
        <Plotly :data="data" :layout="layout" :display-mode-bar="false"></Plotly>
      </v-container>
    </v-content>
    <v-dialog v-model="dialog" max-width="75%">
      <v-card>
        <v-card-title class="headline">Trigger Keys selection</v-card-title>
        <v-card-text>
          <v-treeview v-model="selectedTriggers" selectable :items="availableTriggerKeys"></v-treeview>
        </v-card-text>
        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn color="green darken-1" text @click="dialog = false">
            Close
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
    <v-footer>API: {{ apiEndpoint }} - {{commitHash}} - gitlab.cern.ch/avivace/ratemon-ui</v-footer>
  </v-app>
</template>
<script>
import { Plotly } from 'vue-plotly'
export default {
  name: 'Rates',

  components: {
    Plotly
  },
  data: () => ({
      commitHash: process.env.VUE_APP_GIT_HASH,
      apiEndpoint: 'localhost:8081',
      availableRuns: [305112, 315257, 315259, 315264],
  selectedRun: null,
    selectedTriggers: [ "HLT_PFJet450", "HLT_AK8PFJet200", "HLT_Photon60_R9Id90_CaloIdL_IsoL_DisplacedIdL_PFHT350MinPFJet15", "L1_SingleEG26er2p5", "L1_SingleTau120er2p1" ] ,
    dialog: false,
    availableTriggerKeys: [{
        id: 0,
        name: 'L1',
        children: [, { id: 'L1_DoubleMu_12_5', name: 'L1_DoubleMu_12_5' }, { id: 'L1_SingleTau120er2p1', name: 'L1_SingleTau120er2p1' }, { id: 'L1_SingleJet120', name: 'L1_SingleJet120' }, { id: 'L1_SingleMu22', name: 'L1_SingleMu22' }, { id: 'L1_SingleMu22_EMTF', name: 'L1_SingleMu22_EMTF' }, { id: 'L1_SingleMu16er1p5', name: 'L1_SingleMu16er1p5' }, { id: 'L1_DoubleTau70er2p1', name: 'L1_DoubleTau70er2p1' }, {id:'L1_SingleEG26er2p5',name:'L1_SingleEG26er2p5'}, { id: 'L1_SingleEG40er2p5', name: 'L1_SingleEG40er2p5' }, { id: 'L1_SingleIsoEG28er2p5', name: 'L1_SingleIsoEG28er2p5' }, { id: 'L1_DoubleEG_25_12_er2p5', name: 'L1_DoubleEG_25_12_er2p5' }, { id: 'L1_TripleJet_95_75_65_DoubleJet_75_65_er2p5', name: 'L1_TripleJet_95_75_65_DoubleJet_75_65_er2p5' }],
      },
      {
        id: 1,
        name: 'HLT',
            children: [
             { id: 'HLT_Ele40_WPTight_Gsf', name: 'HLT_Ele40_WPTight_Gsf' }, { id: 'HLT_DoubleEle33_CaloIdL_MW', name: 'HLT_DoubleEle33_CaloIdL_MW' }, { id: 'HLT_Ele23_Ele12_CaloIdL_TrackIdL_IsoVL_DZ', name: 'HLT_Ele23_Ele12_CaloIdL_TrackIdL_IsoVL_DZ' }, { id: 'HLT_IsoMu27', name: 'HLT_IsoMu27' }, { id: 'HLT_Mu17_TrkIsoVVL_Mu8_TrkIsoVVL_DZ', name: 'HLT_Mu17_TrkIsoVVL_Mu8_TrkIsoVVL_DZ' }, { id: 'HLT_Mu23_TrkIsoVVL_Ele12_CaloIdL_TrackIdL_IsoVL', name: 'HLT_Mu23_TrkIsoVVL_Ele12_CaloIdL_TrackIdL_IsoVL' }, { id: 'HLT_Mu23_TrkIsoVVL_Ele12_CaloIdL_TrackIdL_IsoVL_DZ', name: 'HLT_Mu23_TrkIsoVVL_Ele12_CaloIdL_TrackIdL_IsoVL_DZ' }, { id: 'HLT_DoubleMediumChargedIsoPFTau35_Trk1_eta2p1_Reg', name: 'HLT_DoubleMediumChargedIsoPFTau35_Trk1_eta2p1_Reg' }, { id: 'HLT_Photon200', name: 'HLT_Photon200' }, { id: 'HLT_Photon60_R9Id90_CaloIdL_IsoL_DisplacedIdL_PFHT350MinPFJet15', name: 'HLT_Photon60_R9Id90_CaloIdL_IsoL_DisplacedIdL_PFHT350MinPFJet15' }, { id: 'HLT_DoublePhoton70', name: 'HLT_DoublePhoton70' }, { id: 'HLT_AK8PFJet200', name: 'HLT_AK8PFJet200' }, { id: 'HLT_CaloJet500_NoJetID', name: 'HLT_CaloJet500_NoJetID' }, { id: 'HLT_PFJet450', name: 'HLT_PFJet450' }, { id: 'HLT_HT300PT30_QuadJet_75_60_45_40_TripeCSV_p07', name: 'HLT_HT300PT30_QuadJet_75_60_45_40_TripeCSV_p07' }, { id: 'HLT_PFHT430', name: 'HLT_PFHT430' }, { id: 'HLT_PFMET110_PFMHT110_IDTight', name: 'HLT_PFMET110_PFMHT110_IDTight' }
            ],

      }
    ],
    data: [{
      x: [1, 2, 3, 4],
      y: [10, 15, 13, 17],
      type: "scattergl",
      mode: "markers"
    }],
    layout: {
      title: "My graph"
    }
  }),
  mounted: function() {
    console.log("Mounted")
  },
  methods: {
    compute: function() {
      this.$axios.get('http://localhost:5000/', {
        params: {
          text: this.formText
        }
      }).then(function(response) {
        this.value = response.data.positive;
      });
    },
  },
};

</script>