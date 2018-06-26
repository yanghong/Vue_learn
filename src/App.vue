<template>
  <div id="app">
    <div>{{title}}</div>
  </div>
</template>

<script>
export default{
  data (){
    return {
      title:"this is a todo list."
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
html {
  height: 100%
}

body {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100%;
}
</style>
