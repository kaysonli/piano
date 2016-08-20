<template>
    <div id="app">
        <div class="control">
            <input type="checkbox" v-model="full" id="full"><label for="full">完整键盘</label>
        </div>
        <div class="keyboard">
            <group :group="0" v-show="full"></group>
            <group :group="1" v-show="full"></group>
            <group :group="2"></group>
            <group :group="3"></group>
            <group :group="4"></group>
            <group :group="5" v-show="full"></group>
            <group :group="6" v-show="full"></group>
        </div>
    </div>
</template>

<script>
var attachFastClick = require('fastclick');
attachFastClick.attach(document.body);
import Group from './components/Group'
const prefix = 'data:audio/mpeg;base64,';
import {notes} from './notes.js'
const groupKeys = 12;
const base = 2;
export default {
    components: {
        Group
    },
    data() {
        return {
            full: false
        }
    },
    methods: {
        play(keyCode) {
            let keys = [90,88,67,86,66,78,77,65,83,68,70,71,72,74,81,87,69,82,84,89,85];
            if(keys.indexOf(keyCode) < 0) {
                return;
            }
            let whites = [0, 2, 4, 5, 7, 9, 11];
            let index = base + 2 * groupKeys + whites[keys.indexOf(keyCode) % 7] + parseInt(keys.indexOf(keyCode) / 7)*groupKeys;
            let audio = new Audio(prefix + notes[index]);
            audio.play();
        }
    },
    ready() {
        document.body.addEventListener('keydown', e => {
            this.play(e.keyCode);
        });
    }
}
</script>

<style>
html, body {
  height: 100%;
}
body {
    padding: 0;
    margin: 0;
}

.keyboard {
    display: flex;
    margin: 20px;
}
.control {
    text-align: center;
    margin-top: 50px;
}
</style>
