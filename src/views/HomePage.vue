<template>
  <ion-page>
    <ion-header>
      <ion-toolbar>
        <ion-title>Blank</ion-title>
      </ion-toolbar>
    </ion-header>

    <ion-content>
      <ion-list>
        <ion-item ref="oldInput">
          <ion-label position="floating"> Olde Style </ion-label>
          <ion-input></ion-input>
          <ion-note slot="helper">{{ helperText }}</ion-note>
          <ion-note slot="error">{{ errorText }}</ion-note>
        </ion-item>
        <ion-item lines="none">
          <ion-input
            ref="newInput"
            label="The New Hotness"
            label-placement="floating"
            :errorText="errorText"
            :helperText="helperText"
          ></ion-input>
        </ion-item>
        <ion-item lines="none">
          <ion-input
            type="password"
            label="Password"
            label-placement="floating"
          ></ion-input>
        </ion-item>
        <ion-item>
          <ion-button @click="showHelper">Show Helper</ion-button>
          <ion-button color="danger" @click="showError">Show Error</ion-button>
          <ion-button color="secondary" @click="reset">Reset</ion-button>
        </ion-item>
      </ion-list>
      <div class="ion-padding">
        <ion-input
          ref="nakedInput"
          label="I am Naked"
          label-placement="floating"
          fill="solid"
          :errorText="errorText"
          :helperText="helperText"
        ></ion-input>
      </div>
    </ion-content>
  </ion-page>
</template>

<script setup lang="ts">
import {
  IonButton,
  IonContent,
  IonHeader,
  IonInput,
  IonItem,
  IonLabel,
  IonList,
  IonNote,
  IonPage,
  IonTitle,
  IonToolbar,
} from "@ionic/vue";
import { ref } from "vue";

const helperText = ref();
const errorText = ref();
const oldInput = ref(null);
const newInput = ref(null);
const nakedInput = ref(null);

const showError = () => {
  errorText.value = "you went and hosed that up";
  (oldInput.value as any).$el.classList.remove("ion-valid");
  (oldInput.value as any).$el.classList.add("ion-invalid");
  (newInput.value as any).$el.classList.remove("ion-valid");
  (newInput.value as any).$el.classList.add("ion-invalid");
  (nakedInput.value as any).$el.classList.remove("ion-valid");
  (nakedInput.value as any).$el.classList.add("ion-invalid");
};

const showHelper = () => (helperText.value = "you should really do something");

const reset = () => {
  errorText.value = undefined;
  helperText.value = undefined;
  (oldInput.value as any).$el.classList.add("ion-valid");
  (oldInput.value as any).$el.classList.remove("ion-invalid");
  (newInput.value as any).$el.classList.add("ion-valid");
  (newInput.value as any).$el.classList.remove("ion-invalid");
  (nakedInput.value as any).$el.classList.add("ion-valid");
  (nakedInput.value as any).$el.classList.remove("ion-invalid");
};
</script>
