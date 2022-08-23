<template>
  <div class="hello">
    <h1>Auction</h1>
    <button @click="getFootballers()">Premi</button>
    
    <div v-for="(team, index) in teams" :key="index">
      <h1>{{team.team.name}}</h1>
      <img :src="team.team.logo" alt="">
    </div>
  </div>
</template>

<script>
const axios = require('axios').default;
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data() {
    return {
      teams : [],
    }
  },
  methods: {
    getFootballers() {
      axios.get('https://v3.football.api-sports.io/teams', {
                  headers: {
                    'x-apisports-key': 'd1457ed674658a4600ad9d24e8e2c9ed'
                  },
                  params: {
                    'league': 135,
                    'season': 2022
                  }
                })
           .then((response) => {
             console.log(response.data.response);
             this.teams = response.data.response;
           })
           .catch(function (error) {
             console.log(error);
           })
           .then(function () {

           });
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
h3 {
  margin: 40px 0 0;
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
