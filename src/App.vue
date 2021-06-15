<template>
  <div id="app" style="background-color: #A9957B">
    <v-row class="text-center border">
      <v-col>
        <h1 class="font-weight-bold" style="text-align: center; color: #000000; border: 1px solid black">
          IHM API Film
        </h1>
      </v-col>
    </v-row>
    <div id="nav">
      <router-link to="/">Accueil</router-link> |
      <router-link to="/maListe">Ma liste</router-link>
    </div>
    <router-view/>
  </div>
</template>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #000000;
}

#nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #000000;

    &.router-link-exact-active {
      color: orangered;
;
    }
  }
}
</style>
