<template>
  <div id="app">
    <img src="./assets/logo.png">
    <h1>ANA Leaderboard: KP Brand</h1>
    <div class="container" v-for="(p, index) in people">
      <div class="rank">{{index + 1}}</div><person class="person" v-on:increment="incrementScore($event)" :personName="p.name" :profile="p.image" :id="p.id"></person>
    </div>
   
  </div>
</template>

<script>

import person from './person.vue'

export default {
  name: 'app',
  components: { person },
  data () {
    return {
      people: [
        {id: 0, name: "Jorma", image: "image-1.jpg", score: 0 },
        {id: 1, name: "James", image: "image-2.jpg", score: 0 },
        {id: 2, name: "Jenny", image: "image-3.jpg", score: 0 },
        {id: 3, name: "Jane", image: "image-4.jpg", score: 0 },
        {id: 4, name: "Jordan", image: "image-5.jpg", score: 0 },
        {id: 5, name: "Jake", image: "image-6.jpg", score: 0 },
        {id: 6, name: "Jake", image: "image-7.jpg", score: 0 }
      ]
    }
  },

  methods: {
    incrementScore(e){
      this.people[e.id].score ++;
      this.sortArray();
  
    },
    deincrementScore(e){
      this.people[e.id].score --
      this.sortArray();
      
    },
    sorted(){      
      return this.people
    },
    sortArray(){
      this.people.sort(function(a, b){return a.score < b.score})
      console.log(this.people)
      return this.people
    }
  }
}
</script>

<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1, h2 {
  font-weight: normal;
  margin-bottom: 100px;
}
.container {
  width: 100%;
  margin: 0;
  padding: 0;
}
.rank {
  display: inline-block;
  width: 10%;
  float: left;
}
.person {
  float: left;
  display: inline-block;
  width: 80%;
}

a {
  color: #42b983;
}
</style>
