<template>
  <div id="app">
    <div class="container">
      <div class="row">
        <div class="col">
          <img src="./assets/img/logo.png" alt="Logo Espro" class="img-fluid d-block m-auto p-5">
        </div>
    </div>
    </div>
    <Form />
  </div>
</template>

<script>
import Form from './components/Form.vue'

export default {
  name: 'App',
  components: {
    Form
  }
}
</script>

<style lang="scss">

</style>
