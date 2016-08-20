<template>
    <div id="app">
        <div class="keyboard">
            <group :start="12"></group>
            <group :start="24"></group>
            <group :start="36"></group>
            <group :start="48"></group>
        </div>
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

.keyboard {
    display: flex;
    margin: 20px;
}
</style>
