<template>
  <div id="app">
    <div class="banner">
      <img src="https://vuejs.org/images/logo.png" width="100" alt="vue" class="logo" />
      <h1 v-bind:class="{'hide' : hide}">Welcome to Shit.js {{color}}</h1>
      <button type="button" v-on:click="hideContent"> Hide content above! </button>
      <form id="form">
        <button id="button" type="submit" v-bind:disabled="enabled">SUBMIT</button>
        <input type="checkbox" v-model="checkSelected" v-on:change="enabled1">
        <div>The checkbox is checked {{checkSelected}}</div>
      </form>
    </div>
    <div class="bottom">
      To get started, edit
      <code>./src/components/App.vue</code> and save to reload.
      <br/>
      <span class="fade">
        Checkout
        <code>./README.md</code> for more usages.
      </span>
      <form>
        <label for="#name">Your Name:
          <input type="text" v-model="userName">
        </label>
        <label for="#surname">Your Surname:
          <input type="text" v-model="userSurname">
        </label>
        <label for="#email">Your Email:
          <input type="text" v-model="userEmail">
        </label>
        <button type="button" v-on:click="insertUser">Send formulaire</button>

        <label for="#name" style="margin-top:30px">Favorite color:
            <input type="text" v-model="favoriteColor">
          </label>
          <button type="button" v-on:click="insertColor">Send color</button>

        <div style="margin-top:30px">My user details are: {{user}}</div>
        <div style="margin-top:30px">My favorite colors are: {{favoriteColors}}</div>
      </form>
    </div>
  </div>
</template>

<script>

  var userId = 0;

  export default {
    name: 'app',
    data: function () {
      return {
        color: 'magic',
        another: true,
        user: {
            name:'',
            surname:'',
            email:'' 
        },
        enabled: true,
        checkSelected: false,
        hide: false,
        userName: '',
        userSurname: '',
        userEmail: '',
        favoriteColor: '',
        favoriteColors: []
      }
    },
    methods: {
      insertColor: function () {
        this.favoriteColors.push(this.favoriteColor);
      },
      enabled1: function () {
        if (this.checkSelected) {
          this.enabled = false;
        } else {
          this.enabled = true;
        }
      },
      hideContent: function () {
        if (!this.hide) {
          this.hide = true
        } else {
          this.hide = false
        }
      },
      insertUser: function () {
        this.user.name = this.userName;
        this.user.surname = this.userSurname;
        this.user.email = this.userEmail;
        
        /*this.user = {
          'name': this.userName,
          'surname': this.userSurname,
          'email': this.userEmail
        }*/
      }
    }
  }


</script>

<!-- CSS libraries -->
<style src="normalize.css/normalize.css"></style>

<!-- Global CSS -->
<style>
  code {
    font-family: Menlo, Monaco, Lucida Console, Liberation Mono, DejaVu Sans Mono, Bitstream Vera Sans Mono, Courier New, monospace, serif;
    font-size: 0.9em;
    white-space: pre-wrap;
    color: #2c3e50;
  }

  code::before,
  code::after {
    content: '`';
  }

  .hide {
    display: none;
  }
</style>

<!-- Scoped component css -->
<!-- It only affect current component -->
<style scoped>
  #app {
    text-align: center;
  }

  #app h1 {
    color: #2c3e50;
    font-weight: 300;
    margin: 0;
  }

  .banner {
    height: 200px;
    background-color: #f6f6f6;
    padding: 50px 10px;
  }

  .bottom {
    padding: 80px 10px;
    font-size: 24px;
    font-weight: 300;
  }

  .fade {
    font-size: 14px;
  }

  .logo {
    animation: spin 4s 1s infinite linear
  }

  @keyframes spin {
    from {
      transform: rotate(0deg);
    }
    to {
      transform: rotate(360deg);
    }
  }
</style>