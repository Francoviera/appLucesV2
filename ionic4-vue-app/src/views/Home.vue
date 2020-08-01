<template>
  <div>
    <ion-card>
      <ion-card-header>
        <ion-card-title>Bienvenido!</ion-card-title>
        <!-- <ion-card-subtitle>Card Subtitle</ion-card-subtitle> -->
      </ion-card-header>

      <ion-card-content>
        Esta aplicacion desarrollada para Facilitar a los usuarios el poder acceder a las luces de su casa.
      </ion-card-content>
    </ion-card>

    <ion-card>
      <ion-item >
        <ion-icon name="wifi" slot="start"></ion-icon>
        <ion-card-content>
          <p>
            Verifique su conexion antes de elgir por que medio prender las luces ;)
          </p>
        </ion-card-content>
      </ion-item>
    </ion-card>

    <ion-card>
      <ion-item >
        <ion-icon name="warning" slot="start"></ion-icon>
        <ion-card-content>
          <p>
            La opcion Remota
          </p>
          <p>
            Esto permite acceder a las luces desde otro lugar fuera de su casa, con conexion a internet
          </p>
        </ion-card-content>
      </ion-item>
    </ion-card>
    <ion-card>
      <ion-item >
        <ion-icon name="warning" slot="start"></ion-icon>
        <ion-card-content>
          <p>
            La opcion Local
          </p>
          <p>
            No es necesaria la conexion a internet y es mas rapida
          </p>
        </ion-card-content>
      </ion-item>
    </ion-card>
  </div>
</template>
