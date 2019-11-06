<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

/**
 * Import client from Ditto
 */
import {DittoDomClient,DomHttpBasicAuth} from '@eclipse-ditto/ditto-javascript-client-dom_1.0-pre'

export default {
  name: 'app',
  components: {
    HelloWorld
  }
}

const client =  DittoDomClient.newHttpClient()
            .withTls()
            .withDomain('example.com')
            .withAuthProvider(DomHttpBasicAuth.newInstance("username", 'password'))
            .apiVersion2()
            .build();
client.getThingsHandle();


</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
