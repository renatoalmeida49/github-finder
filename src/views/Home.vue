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
      class="mx-auto"
      align="center"
    >
      <v-card
        max-width="374"
        align="center"
      >
        <v-avatar
          size="120"
        >
          <img :src="portfolio.avatar_url" alt="Foto de perfil" />
        </v-avatar>

        <v-card-title
          align="center"
          style="justify-content: center"
        >
          {{ portfolio.name }}
        </v-card-title>

        <v-card-text>
          <div>@{{ portfolio.login }}</div>

          <div>{{ portfolio.bio }}</div>
        </v-card-text>

        <v-divider></v-divider>

        <v-card-text>
          <p><v-icon>mdi-map-marker</v-icon>{{ portfolio.location }}</p>

          <p><v-icon>mdi-account-multiple</v-icon> {{ portfolio.followers }} seguidores - {{ portfolio.following }} seguindo</p>
        </v-card-text>
      </v-card>
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
              this.getRepositories()
            })
        }
      },
      getRepositories() {
        console.log('Buscando repositórios')
      }
    }
  }
</script>
