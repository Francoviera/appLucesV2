<template>
  <div>
    <vue-speech lang="es-AR" @onTranscriptionEnd = "onEnd" style="display:none" />
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
        <ion-item v-for="luz of lugares" v-bind:key="luz.ipLocal">
          <ion-label>{{luz.nombre}}</ion-label>
          <ion-button color="light" v-show="!luz.encendida" @click="encender(luz)">Encender</ion-button>
          <ion-button color="dark" v-show="luz.encendida" @click="apagar(luz)">Apagar</ion-button>
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
        lugares: [],
        conexion_local: true,
      }
    },
    created(){
      let datosDB= JSON.parse(localStorage.getItem('lugares'));
      if(datosDB === null){
        this.lugares = [];
      }else{
        this.lugares = datosDB;
      }

    },
    methods:{
      onEnd  ( {  lastSentence   } )  { 

        let array= lastSentence.split(' ');
        console.log(array);
        if(array[0] === 'encender'){
          if(array[1] === 'todo'){
            this.encenderTodo();
          }else{
            this.encender(array[1]);
          }
        }
        if(array[0] === 'Apagar'){
          if(array[1] === 'todo'){
            this.apagarTodo();
          }else{
            this.apagar(array[1]);
          }
        }
      },
      encender(luz){
        console.log(luz);
      },
      apagar(luz){
        console.log(luz);
      },
      encenderTodo(){

      },
      apagarTodo(){

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