<template>
    <div>
        <form @submit.prevent="agregar">
            <ion-item>
                <ion-label position="floating">Nombre</ion-label>
                <ion-input class="form-control" :value="nombre" @input= "nombre = $event.target.value"></ion-input>
            </ion-item>

            <ion-item>
                <ion-label position="floating">IP Local</ion-label>
                <ion-input class="form-control" :value="ipLocal" @input= "ipLocal = $event.target.value"></ion-input>
            </ion-item>

            <ion-item>
                <ion-label position="floating">IP Remota</ion-label>
                <ion-input class="form-control" :value="ipRemota" @input= "ipRemota = $event.target.value"></ion-input>
            </ion-item>

            <ion-card-content>
                <ion-button type="submit" expand="block">Agregar</ion-button>
            </ion-card-content>
            
            <ion-card>
                <ion-card-header>
                    <ion-card-subtitle>Luces</ion-card-subtitle>
                    <!-- <ion-card-title>Card Title</ion-card-title> -->
                </ion-card-header>

                <ion-card-content>
                    <ion-list>
                        <ion-item v-for="luz of lugares" v-bind:key="luz.ipLocal">
                            <ion-label>{{luz.nombre}}</ion-label>
                            <ion-button size="small" color="danger" @click="eliminar(luz.ipLocal)">Eliminar</ion-button>
                        </ion-item>
                    </ion-list>
                </ion-card-content>
            </ion-card>
        </form>
    </div>
</template>
<script lang="ts">
    export default {
        data(){
            return{
                lugares: [],
                nombre: ' ',
                encendida: ' ',
                ipLocal: ' ',
                ipRemota: ' ',

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
            agregar(){
                this.lugares.push({
                    nombre: this.nombre,
                    ipLocal: this.ipLocal,
                    ipRemota: this.ipRemota,
                    encendida: false
                });
                this.nombre= '';
                this.ipLocal= '';
                this.ipRemota= '';
                localStorage.setItem('lugares', JSON.stringify(this.lugares));
            },
            eliminar(index){
                this.lugares.splice(index, 1);
                localStorage.setItem('lugares', JSON.stringify(this.lugares));
            }
        }
    }
</script>