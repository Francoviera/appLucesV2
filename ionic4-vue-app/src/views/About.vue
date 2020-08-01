<template>
  <div>
    <!-- <vue-speech lang="es-AR" @onTranscriptionEnd = "onEnd" style="display:none" /> -->
    <ion-card>
      <ion-card-header>
        <ion-card-subtitle>App Viera</ion-card-subtitle>
        <ion-card-title>Luces de la Casa</ion-card-title>
      </ion-card-header>

      <ion-card-content>
        <ion-item>
          <ion-label>Conexion</ion-label>
          <ion-select placeholder="Seleccione" v-model="conexion_local">
            <ion-select-option value= true >Local</ion-select-option>
            <ion-select-option value= false >Remota</ion-select-option>
          </ion-select>
        </ion-item>
      </ion-card-content>

      <ion-card-content>
        <ion-item>
          <ion-label>Cocina</ion-label>
          <ion-button color="light" v-show="!cocina_on" @click="prenderCocina()">Encender</ion-button>
          <ion-button color="dark" v-show="cocina_on" @click="apagarCocina()">Apagar</ion-button>
        </ion-item>  
        <ion-item>
          <ion-label>Baño</ion-label>
          <ion-button color="light" v-show="!baño_on" @click="prenderBaño()">Encender</ion-button>
          <ion-button color="dark" v-show="baño_on" @click="apagarBaño()">Apagar</ion-button>
        </ion-item>  
        <ion-item>
          <ion-label>Comedor</ion-label>
          <ion-button color="light" v-show="!comedor_on" @click="prenderComedor()">Encender</ion-button>
          <ion-button color="dark" v-show="comedor_on" @click="apagarComedor()">Apagar</ion-button>
        </ion-item>  
        <ion-item>
          <ion-label>Pieza</ion-label>
          <ion-button color="light" v-show="!pieza_on" @click="prenderPieza()">Encender</ion-button>
          <ion-button color="dark" v-show="pieza_on" @click="apagarPieza()">Apagar</ion-button>
        </ion-item>  
      </ion-card-content>
    </ion-card>
  </div>
</template>
<script>
  // import axios from 'axios';
  
  export default {
    data: function(){
      return{
        lugares: '',
        cocina_on: false,
        pieza_on: false,
        baño_on: false,
        comedor_on: false,
        conexion_local: true,
      }
    },
    created: function(){
      let datosDB= JSON.parse(localStorage.getItem('lugares'));
      if(datosDB === null){
        this.lugares = [];
      }else{
        this.lugares = datosDB;
      }
      console.log(datosDB);
    },

    methods:{
      onEnd  ( {  lastSentence   } )  { 

        if(lastSentence === 'encender cocina'){
          this.prenderCocina();
        }
        if(lastSentence === 'Apagar cocina'){
          this.apagarCocina();
        }
        if(lastSentence === 'encender baño'){
          this.prenderBaño();
        }
        if(lastSentence === 'Apagar baño'){
          this.apagarBaño();
        }
        if(lastSentence === 'encender pieza'){
          this.prenderPieza();
        }
        if(lastSentence === 'Apagar pieza'){
          this.apagarPieza();
        }
        if(lastSentence === 'encender comedor'){
          this.prenderComedor();
        }
        if(lastSentence === 'Apagar comedor'){
          this.apagarComedor();
        }
        if(lastSentence === 'Apagar todo'){
          this.apagarCocina();
          this.apagarBaño();
          this.apagarComedor();
          this.apagarPieza();
        }
        if(lastSentence === 'encender todo'){
          this.prenderPieza();
          this.prenderComedor();
          this.prenderBaño();
          this.prenderCocina();
        }
      },
      prenderCocina(){
        this.cocina_on= true;
        // axios.get(this.ipCocina+'/cocina=on').then(response=>{
        //   this.cocina_on= true;
        // }); 
      },
      apagarCocina(){
        this.cocina_on= false;
      },
      prenderBaño(){
        this.baño_on= true;
      },
      apagarBaño(){
        this.baño_on= false;
      },
      prenderComedor(){
        this.comedor_on= true;
      },
      apagarComedor(){
        this.comedor_on= false;
      },
      prenderPieza(){
        this.pieza_on= true;
      },
      apagarPieza(){
        this.pieza_on= false;
      },
    }
  }
</script>