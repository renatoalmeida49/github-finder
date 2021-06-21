<template>
<v-container>
  <v-row>
    <v-col
      cols="12"
      align="center"
    >
      <h1>Github Finder</h1>
    </v-col>

    <v-col
      cols="12"
      align="center"
    >
      <v-text-field
        placeholder="Pesquise um perfil no Github"
        filled
        rounded
        dense
        clearable
        v-model="search"
        @keyup.enter="getProfile"
      ></v-text-field>

      <v-btn
        elevation="2"
        rounded
        @click="getProfile"
      >Pesquisar</v-btn>
    </v-col>
  </v-row>
  <v-row v-if="portfolio">
    <v-col
      cols="12"
    >
      <v-avatar
        size="62"
      >
        <img :src="portfolio.avatar_url" alt="Foto de perfil" />
      </v-avatar>

      <h1>{{ portfolio.name }}</h1>
      <h2>@{{ portfolio.login }}</h2>

      <p>{{ portfolio.bio }}</p>

      <p><v-icon>mdi-map-marker</v-icon>{{ portfolio.location }}</p>

      <p><v-icon>mdi-account-multiple</v-icon> {{ portfolio.followers }} seguidores - {{ portfolio.following }} seguindo</p>
    </v-col>
  </v-row>
</v-container>
</template>

<script>
  

  export default {
    name: 'Home',
    data() {
      return {
        search: null,
        portfolio: null
      }
    },
    components: {
      
    },
    methods: {
      getProfile() {
        if(this.search !== null) {
          fetch(`https://api.github.com/users/${this.search}`)
            .then(response => response.json())
            .then(response => {
              this.portfolio = response
            })
        }
      }
    }
  }
</script>
