<template>
    <div class="nav-head">
        <h1 class="main" @click="changeScreen(false)">Kicking Assets</h1>
        <h2 @click="changeScreen('win')" class="win-calc">Win Calculator</h2>
        <a href="https://www.google.com/"><h2 class="graphs">Graphs</h2></a>
        <h2 @click="changeScreen('summary')" class="summary">Summary</h2>
    </div>
</template>
<script>
export default {
    props: ['changeScreen']
}
</script>
<style scoped>
.nav-head {
    padding-top: 10px;
    font-size: 40px;
    display: flex;
    align-items: baseline;
    background-color: #0c2360;
    margin-left: -400px;
    padding-left: 400px;
    margin-right: -400px;
    padding-right: 400px;
    box-shadow: 0px 10px 10px 0px;
    }
.main {
    font-family: "Lucida Console", Monaco, monospace;
    color: white;
}
.main:hover {
    color: gray;
    cursor: pointer;
}
h2 {
    font-size: 25px;
    color: white;
}
.win-calc {
    margin-left: 90px;
    margin-right: 40px;
    padding: 5px 10px 5px 10px;
    border-radius: 5px;
}
.win-calc:hover {
    color: #4971af;
    cursor: pointer;
    background-color: white;
}
.graphs {
    padding: 5px 10px 5px 10px;
    border-radius: 5px;
}
.graphs:hover {
    cursor: pointer;
    color: #4971af;
    background-color: white;

}
a {
    text-decoration: none;
}
.summary {
    padding: 5px 10px 5px 10px;
    border-radius: 5px;
    margin-left: 40px;
}
.summary:hover {
    cursor: pointer;
    color: #4971af;
    background-color: white;
}
</style>