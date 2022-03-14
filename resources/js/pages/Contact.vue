<template>
  
<div class="container">
  <div class="row">
    <div class="col">
      <div v-if="success==true" class="alert alert-success" role="alert">
        Messaggio inviato correttamente
      </div>
      
      <form @submit.prevent="postMessage()">
        <div class="mb-3">
          <label for="inputName" class="form-label">Nome</label>
          <input v-model="name" type="text" class="form-control" id="inputName" aria-describedby="nameHelp">
          <div class="mt-1" v-if="errors.name">
            <div v-for="error, index in errors.name" class="alert alert-danger" role="alert" :key="'name-err-'  + index">
              {{error}} 
            </div>
          </div>
        </div>
        
        <div class="mb-3">
          <label for="inputEmail" class="form-label">Indirizzo e-mail</label>
          <input v-model="email" type="email" class="form-control" id="inputEmail" aria-describedby="emailHelp">
          <div id="emailHelp" class="form-text">Questo indirizzo non verr&agrave; condiviso con nessun altro.</div>
          <div class="mt-1" v-if="errors.email">
            <div v-for="error, index in errors.email" class="alert alert-danger" role="alert" :key="'email-err-'  + index">
              {{error}} 
            </div>
          </div>
        </div>
          
        <div class="mb-3">
          <label for="inputText" class="form-label">Messaggio</label>
          <textarea v-model="message  " class="form-control" id="inputText" cols="20" rows="10"></textarea>
          <div class="mt-1" v-if="errors.message">
            <div v-for="error, index in errors.message" class="alert alert-danger" role="alert" :key="'message-err-'  + index">
              {{error}} 
            </div>
          </div>
        </div>

        <button type="submit" class="btn text-light btn-primary" :class="sendingEmail ? 'disabled': ''">{{sendingEmail ? 'Sto inviando' : 'Invia'}}</button>
      </form>
    </div>
  </div>
</div>

</template>

<script>
import axios from 'axios';

export default {
    name: 'Contact',
    data() {
      return {
        name: null,
        email: null,
        message: null,
        success: false,
        errors: [],
        sendingEmail: false,
      }
    },
    methods: {
      postMessage() {
        const vueThis = this;
        this.success = false;
        if (!this.sendingEmail) {
          this.sendingEmail = true;
          axios.post('api/contact',
            {
              name: vueThis.name,
              email: vueThis.email,
              message: vueThis.message,
            }).then(response => {
              vueThis.sendingEmail = false;
              if (response.data.success) {
              vueThis.success = true;
              vueThis.name = null;
              vueThis.email = null;
              vueThis.message = null;
              vueThis.errors = [];
            } else {
              vueThis.sendingEmail = false;
              vueThis.success = false;
              vueThis.errors = response.data.errors;
            }
          })
          .catch(error => {console.log(error.response.data)});
        }
        
      },
    }
}
</script>

<style>

</style>