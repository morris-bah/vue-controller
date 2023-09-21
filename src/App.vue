<script>

import { ref } from 'vue'
import TabsWrapper from './components/TabsWrapper.vue'
import TabItem from './components/TabItem.vue'
import 'status-indicator/styles.css';
import MainPanel from './components/MainPanel.vue'

export default {
    name: 'App',
    components: {
        TabsWrapper,
        TabItem,
        MainPanel,
    },
    setup(_, context) {

        const iap2InAngOffX   = ref(10);
        const iap2InAngOffY   = ref(20);
        const iap2InAlignOffX = ref(30);
        const iap2InAlignOffY = ref(40);
        const iap3InAngOffX   = ref(50);
        const iap3InAngOffY   = ref(60);
        const iap3InAlignOffX = ref(70);
        const iap3InAlignOffY = ref(80);
        const iruInAngOffX    = ref(90);
        const iruInAngOffY    = ref(100);
        const iruInAlignOffX  = ref(110);
        const iruInAlignOffY  = ref(120);

        return {
            iap2InAngOffX,
            iap2InAngOffY,
            iap2InAlignOffX,
            iap2InAlignOffY,
            iap3InAngOffX,
            iap3InAngOffY,
            iap3InAlignOffX,
            iap3InAlignOffY,
            iruInAngOffX,
            iruInAngOffY,
            iruInAlignOffX,
            iruInAlignOffY,
        };
    }
}

</script>

<template>
    <v-app id="app">
        <img src="./assets/navsea.jfif"  aria-hidden="false" width="70"/>
        <v-app-bar >
            <v-toolbar-title>ODIN IAP/IRU Alignment</v-toolbar-title>
        </v-app-bar>
        <v-container>
            <!-- Indicator labels -->
            <v-row class="v-row-short" justify="center">
                <v-col cols="1"> Data Conn</v-col>
                <v-col cols="1"> Image Conn</v-col>
                <v-col cols="1"> Cam 232</v-col>
                <v-col cols="1"> Cam Fval</v-col>
                <v-col cols="1"> Config Valid</v-col>
                <v-col cols="1"> Torque Fault</v-col>
            </v-row>
            <!-- Indicator LEDs -->
            <v-row class="v-row-short" justify="center">
                <v-col cols="1"><status-indicator id="DataConn" active pulse></status-indicator> </v-col>
                <v-col cols="1"><status-indicator id="ImgConn"  intermediary pulse></status-indicator> </v-col>
                <v-col cols="1"><status-indicator id="CamRs232" positive pulse></status-indicator> </v-col>
                <v-col cols="1"><status-indicator id="CamFval"  negative pulse></status-indicator> </v-col>
                <v-col cols="1"><status-indicator id="ConfigVal" negative pulse></status-indicator> </v-col>
                <v-col cols="1"><status-indicator id="TorqueFault" negative pulse></status-indicator> </v-col>
            </v-row>
            <!-- Control Panels for devices -->
            <v-row justify="center">
                <v-col cols="12" align-self="center">
                    <TabsWrapper class="tab-box">
                        <TabItem title="IAP 2&quot" class="tabitem">
                            <MainPanel id="IAP2In" 
                            :AngOffX.value=  iap2InAngOffX
                            :AngOffY.value=  iap2InAngOffY
                            :AlignOffX.value=iap2InAlignOffX
                            :AlignOffY.value=iap2InAlignOffY
                            />
                        </TabItem>
                        <TabItem title="IAP 3&quot">
                            <MainPanel  id="IAP3In"
                            :AngOffX.value=  iap3InAngOffX
                            :AngOffY.value=  iap3InAngOffY
                            :AlignOffX.value=iap3InAlignOffX
                            :AlignOffY.value=iap3InAlignOffY
                             />
                        </TabItem>
                        <TabItem title="IRU">
                            <MainPanel  id="IRU"
                            :AngOffX.value=  iruInAngOffX
                            :AngOffY.value=  iruInAngOffY
                            :AlignOffX.value=iruInAlignOffX
                            :AlignOffY.value=iruInAlignOffY
                             />
                        </TabItem>
                    </TabsWrapper>
                </v-col>
            </v-row>
            <!-- Camera control panel and image -->
            <v-row justify="center">
            <v-col cols="5" sm="5" md="5">
                <v-container>
                    <v-row class="v-row-short" justify="start">
                        <v-col cols="7"><label for="WindowX" >Window X</label></v-col>
                        <v-col cols="3"><input type="number" id="WindowX" class="num-input-cam"/></v-col>
                    </v-row>
                    <v-row class="v-row-short" justify="start">
                        <v-col cols="7"><label for="WindowY">Window Y</label></v-col>
                        <v-col cols="3"><input type="number" id="WindowY" class="num-input-cam"/></v-col>
                    </v-row>
                    <v-row class="v-row-short" justify="start">
                        <v-col cols="7"><label for="OffsetX">Offset X</label></v-col>
                        <v-col cols="3"><input type="number" id="OffsetX" class="num-input-cam"/></v-col>
                    </v-row>
                    <v-row class="v-row-short" justify="start">
                        <v-col cols="7"><label for="OffsetY">Offset Y</label></v-col>
                        <v-col cols="3"><input type="number" id="OffsetY" class="num-input-cam"/></v-col>
                    </v-row>
                    <v-row class="v-row-short" justify="start">
                        <v-col cols="7"><label for="ExpTime">Exp. Time</label></v-col>
                        <v-col cols="3"><input type="number" id="ExpTime" class="num-input-cam"/></v-col>
                    </v-row>
                    <v-row class="v-row-short" justify="start">
                        <v-col cols="7"><label for="FrameRate">Frame Rate</label></v-col>
                        <v-col cols="3"><input type="number" id="FrameRate" class="num-input-cam"/></v-col>
                    </v-row>
                </v-container> 
            </v-col>
            <v-col cols="6" sm="6" md="6" justify="left">
                <div>
                    <!-- <video id="video" width="240" height="180" autoplay>
                        <source src="/beams2.mp4" type="video/mp4">
                    </video> -->
                <img src="./assets/lighthousesq.jpg" width="250" />
            </div>
            </v-col>
        </v-row>
    </v-container>
    </v-app>
</template>

<style>
* {
    box-sizing: border-box;
}

#app {
    width: 100%;
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: var(--v-theme-on-primary);
    background-color: var(--v-theme-background); 
    margin-top: 60px;
}

.v-row-short {
    max-height: 40px;
}

.tab-box {
    display: flex;
    flex-direction: column;
    width: 100%;
    height: 50%;
    color: black;
    font-weight: bold;
    background-color: var(--v-theme-background);
}

.tabitem { 
    padding: 5px;
    color: var(black);
    background-color: grey;
}

.num-input-cam {
    color: black;
    font-weight: bold;
    background-color: #cacaca;
    width: 80px;
}

v-label {
  display: inline-block;
  margin-left: 5px;
  width: 50px;
  color: var(--v-theme-text-dark);
}

</style>
