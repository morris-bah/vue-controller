<script>
import { ref, watch, toRefs } from 'vue';

export default {
    name: 'MainPanel',

    setup(_, context) {
        const AngOffX = ref(10);
        const AngOffY = ref(20);
        const AlignOffX = ref(30);
        const AlignOffY = ref(40);

        return {
            AngOffX,
            AngOffY,
            AlignOffX,
            AlignOffY,
        };
    }
}
</script>

<template>    
    <v-container class="text-left">
        <v-row dense align="baseline">
            <v-col cols="4">
                <v-label for="AngOffsetX">Angle Offset X</v-label>
            </v-col>
            <v-col cols="1" offset="1">
                <input density="compact" type="number" v-model.number=AngOffX id="AngOffsetX" class="num-input"/>
            </v-col>
        </v-row>
        <v-row dense>
            <v-col cols="4">
                <v-label for="AngOffsetY">Angle Offset Y</v-label>
            </v-col>
            <v-col cols="1" offset="1">
                <input type="number" v-model.number=AngOffY id="AngOffsetY" class="num-input" />
            </v-col>
        </v-row>
        <v-row dense>
            <v-col cols="4">
                <v-label for="AlignOffX">Align Offset X</v-label>
            </v-col>
            <v-col cols="1" offset="1">
                <input type="number" v-model.number=AlignOffX id="AlignOffX" class="num-input" />
            </v-col>
        </v-row>
        <v-row dense>
            <v-col cols="4">
                <v-label for="AlignOffY">Align Offset Y</v-label>
            </v-col>
            <v-col cols="1" offset="1">
                <input type="number" v-model.number=AlignOffY id="AlignOffY" class="num-input" />
            </v-col>
        </v-row>
        <v-row dense>
            <v-col cols="4">
                <v-label for="ModeSel">Mode</v-label>
            </v-col>
            <v-col cols="1" offset="1">
                <input type="number" id="ModeSel" class="num-input" />
            </v-col>
        </v-row>
        <v-row justify="center" >
            <v-col cols="12" sm="5" md="4">
                <v-btn class="vbtn" block rounded="lg" size="large">Center Beam</v-btn>
            </v-col>
        </v-row>
    </v-container>
</template>

<style >
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

.num-input {
    color: var(--v-theme-text-color);
    background-color: #cacaca;
    width: 80px;
    max-width: 80px;
}

v-label {
  display: inline-block;
  margin-left: 5px;
  width: 50px;
  color: var(--v-theme-text-dark);
}

</style>
