<template>
  <div id="app">
    <Times />
  </div>
</template>

<script>
import Times from './components/Time/Times.vue'

export default {
  name: 'App',
  components: {
    Times
  }
}
</script>

<style>
@import url("https://fonts.googleapis.com/css?family=Montserrat:400,700");
body {
  background-color: #eee;
  font-family: "Montserrat", sans-serif;
  display: grid;
  justify-items: center;
}

body, html {
  margin: 0;
  height: 100%;
}

#app {
}

.btn_Danger{
  background-color: #fa4430;
  color: white;
}

.btn{
  border: 1px solid black;
  cursor: pointer;
  padding: 10px 20px;
  
  font-weight: bold;
  border-radius: 5px;
  border-bottom: 3px solid black;
}

.btn:hover{
  margin-top: 2px;
  border-bottom: 1px solid black;
}
.btn_Danger:hover{
  text-shadow: 1px 1px 1px black;
  margin-top: 2px;
  border-bottom: 1px solid black;
}

table {
  margin: 0;
  padding: 0;
  list-style-type: none;
  width: 100%;
}

table thead th{
  background-color: rgb(184, 208, 216) !important;
  font-size: 1.2em;
  padding: 10px 0;
  text-align: center !important;
}

table tbody td input{
  padding: 10px 20px;
  display: inline;
}

table tr td{
  padding: 20px;
  font-size: 1.3em;
  background-color: #e0edf4;
  margin-bottom: 2px;
  color: #3e5252;
}
.colPequeno {
  width: 5%;
}
</style>