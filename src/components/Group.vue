<template>
    <div class="group">
        <button class="white" v-for="n in 7" data-note="{{n}}" @click="play"></button>
        <button class="black" v-for="n in 5"></button>
        <audio src="../assets/audio/German Concert D 021 083.ogg"></audio>
        <div class="audios">
            <!-- <audio src="{{aud}}" v-for="aud in audios"></audio> -->
        </div>
    </div>
</template>

<script>
export default {
    props: {
        start: {
            type: Number,
            default: 1
        }
    },
    data() {
        return {
            // note: changing this line won't causes changes
            // with hot-reload because the reloaded component
            // preserves its current state and we are modifying
            // its initial state.
        }
    },
    computed: {
        audios() {
            let files = [];
            for (var i = 0, ln = 12; i < ln; i++) {
                files.push(this.parseSrc(i));
            }
            return files;
        }
    },
    methods: {
        play(arg) {
            console.log(arg.target);
        },
        parseSrc(index) {
            let number = this.start + index;
            let ordinal = ('000' + number).slice(-3);
            let fileName = `../assets/audio/German Concert D ${ordinal} 083.ogg`;
            return fileName;
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
    }
    button {
        /*width: 14.29%;*/
        flex: 1;
        height: 300px;
        display: inline-block;
        border: 1px solid #ccc;
        outline: 0;
        padding: 0;
        box-sizing: border-box;
    }
    .white:active {
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
