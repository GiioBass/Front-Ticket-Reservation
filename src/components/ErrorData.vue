<template>
  <section>
    <div class="alert alert-danger" role="alert">
      <p>{{ message }}</p>
      <p>Lo sentimos, no es posible obtener la información en este momento, por favor intente nuevamente mas tarde</p>
    </div>
  </section>
</template>

<script>
export default {
  name: "ErrorData",
  props: {
    message: null
  }
}
</script>

<style scoped>

</style>