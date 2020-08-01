<template>
  <div id="app">
    <div id="nav">
    </div>
    <div>
      <ion-tabs>
        <ion-tab tab="configuracion">
          <ion-header translucent>
            <ion-toolbar>
              <ion-title>Configuracion</ion-title>
            </ion-toolbar>
          </ion-header>

          <ion-content fullscreen class="ion-padding">
            <Configuracion />
          </ion-content>
        </ion-tab>

        <ion-tab tab="Luces">
          <ion-header translucent>
            <ion-toolbar>
              <ion-title>Luces</ion-title>
            </ion-toolbar>
          </ion-header>

          <ion-content fullscreen class="ion-padding">
            <Herramientas />
          </ion-content>
        </ion-tab>

        <ion-tab-bar slot="bottom">
          <ion-tab-button tab="configuracion">
            <ion-label>Configuracion</ion-label>
            <ion-icon name="settings"></ion-icon>
          </ion-tab-button>
          <ion-tab-button tab="Luces">
            <ion-label>Luces</ion-label>
            <ion-icon name="bulb"></ion-icon>          
          </ion-tab-button>
        </ion-tab-bar>
      </ion-tabs>
    </div>
    <router-view/>
  </div>
</template>
<script>
import Herramientas from '@/components/HerramientasComponent.vue'
import Configuracion from '@/components/ConfiguracionComponent.vue'
export default {
  components:{
    Herramientas,
    Configuracion
  }
}
</script>
<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
