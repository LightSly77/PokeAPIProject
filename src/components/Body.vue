<template>
  <div>
    <ul class="text-center spacing-top">
      <li v-for="pokemon in pokemons" :key="pokemon" class="list-group-item align-items-center spacing-bottom">
        <div>
          <img :src="pokemon.sprite" />
        </div>
        <div>
          <h2>{{pokemon.name}}</h2>
          <p>{{pokemon.type}} type</p>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "Body",
  data() {
    return {
      pokemons: []
    };
  },
  created() {
    var numbers = []
    var max = 0

    while(max < 10){
      numbers[max] = Math.floor(Math.random() * 900);
      max++
    }
    
    numbers.forEach(element => {
      this.getPokemons(element);
    });
  },
  methods: {
    async getPokemons(rand) {
      const firstPokemonUrl = await this.axios.get(
        "https://pokeapi.co/api/v2/pokemon/?offset=0&limit=900"
      );

      const secondPokemonUrl = await this.axios.get(
        firstPokemonUrl.data.results[rand].url
      );

      let pokemonobject = {};
      pokemonobject.name = secondPokemonUrl.data.name;
      pokemonobject.sprite = secondPokemonUrl.data.sprites.front_default;
      pokemonobject.type = secondPokemonUrl.data.types[0].type.name;
      this.pokemons.push(pokemonobject);
    }
  }
};
</script>

<style>

h2, p::first-letter {
  text-transform: capitalize;
}

li{
  width: 350px;
  margin-bottom: 20px;
}
ul{
    display: flex;
    justify-content: space-around;
    flex-wrap: wrap;
    padding-left: 0px;
}

.spacing-top{
  margin-top:80px;
}

.spacing-bottom{
  margin-bottom:10px;
}
</style>