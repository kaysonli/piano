<template>
    <div id="app">
        <hello></hello>
        <group></group>
    </div>
</template>

<script>
import Hello from './components/Hello'
import Group from './components/Group'
export default {
    components: {
        Hello, Group
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


</style>
