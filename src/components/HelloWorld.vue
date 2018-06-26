<template>
  <div class="hello">
    <h1 v-text="title"></h1>
    <input v-model="newItem" v-on:keyup.enter="addNew">
    <ul>
      <li v-for="item in items" v-bind:class="{finished: item.isFinished}" v-on:click="toggleFinish(item)">
        {{item.label}}
      </li>
      <br>
    </ul>
  </div>
</template>

<script>
import Store from '../store'

export default {
  name: 'HelloWorld',
  data () {
    return {
      title: 'This is a TODO list.',
      items:Store.fetch(),
      newItem:''
    }
  },
  watch:{
    items:{
        handler: function (items){
        Store.save(items)
      },
      deep: true
    }
  },
  methods:{
    toggleFinish:function (item){
      item.isFinished = !item.isFinished
    },
    addNew:function (item){
      this.items.push({
        label:this.newItem,
        isFinished:false
      })
      this.newItem = ''
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.finished {
  text-decoration: line-through;
}

h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
