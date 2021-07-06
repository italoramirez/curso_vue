<template>
  <my-input 
    name="Usuario" 
    :rules="{ required: true, min: 5 }"
    :value="usuario.value"
    @update="update" 
  />
  <my-input 
    name="Password" 
    :rules="{ required: true, min: 10 }"
    :value="password.value">
  >
  </my-input>
  <Button 
    color="white" 
    background="darkslateblue" 
    :disabled="!valid" 
  />
</template>

<script>

import Button from './components/Button.vue'
import MyInput from './components/MyInput.vue'

export default {
  name: 'App',
  components: {
    Button,
    MyInput
  },
  data () {
    return {
      valid: true,
      usuario: {
        value: 'users',
        valid: false
      },
      password: {
        value: '',
        valid: false
      }
    }
  },
  methods: {
    update ( payload ) {
      console.log(payload);
      this[payload.name.toLowerCase()].value = payload.value;
    }
  }

}
</script>

<style>

  div {
    display: flex;
    flex-direction: column;
  }

  body {
    font-family: arial;
  }
</style>
