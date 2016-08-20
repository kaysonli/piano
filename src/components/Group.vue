<template>
    <div class="group">
        <button :class="{'white': whites.indexOf(n) > -1, 'black': blacks.indexOf(n) > -1}" v-for="n in 12" :style="{ left: calcLeft(n) + '%' }" data-note="{{start+n}}" @click="play(start+n)"><span v-show="n === 0">C</span></button>
    </div>
</template>

<script>
import {notes} from '../notes.js';
const prefix = 'data:audio/mpeg;base64,';
const base = 2;
const keys = 12;
export default {
    props: {
        group: {
            type: Number,
            default: 0
        }
    },
    data() {
        return {
            // note: changing this line won't causes changes
            // with hot-reload because the reloaded component
            // preserves its current state and we are modifying
            // its initial state.
            blacks: [1, 3, 6, 8, 10],
            whites: [0, 2, 4, 5, 7, 9, 11]
        }
    },
    computed: {
        start() {
            return this.group * keys;
        }
    },
    methods: {
        play(index) {
            var audio = new Audio(prefix + notes[index + base]);
            audio.play();
        },
        calcLeft(index) {
            var unit = 14.29;
            var i = this.blacks.indexOf(index);
            if(i < 2) {
                return unit * (0.75 + i);
            }
            return unit * (1.75 + i);
        },
        click(index) {

        }
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    .group {
        font-size: 0;
        position: relative;
        display: flex;
        flex-grow: 1;
    }
    button {
        width: 14.29%;
        flex: 1;
        height: 300px;
        display: inline-block;
        border: 1px solid #ccc;
        outline: 0;
        padding: 0;
        box-sizing: border-box;
    }
    button > span {
        position: absolute;
        bottom: 10px;
    }
    .white:active,
    .white.active {
        background: #ececec;
    }
    .white {
        background: #fff;
    }
    .black {
        background: #000;
        border-color: #000;
        height: 150px;
        width: 7.15%;
        position: absolute;
    }
</style>
