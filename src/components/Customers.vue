<template>
  <div v-if="errored">
    <errorData message="Esto es un error al cargar"></errorData>
  </div>
  <div v-else class="container">
    <spinner v-if="loading"></spinner>
    <div v-else class="card">
      <div class="card-header">
        Customers
      </div>
      <div class="card-body">
        <table class="table">
          <thead>
          <tr>
            <th scope="col">Identification_number</th>
            <th scope="col">Name</th>
            <th scope="col">e-mail</th>
            <th scope="col">Phone</th>
            <th scope="col">Address</th>
          </tr>
          </thead>
          <tbody>
          <tr :key="customer.id" v-for="customer in customers">
            <td>{{ customer.identification_number }}</td>
            <td>{{ customer.name }}</td>
            <td>{{ customer.email }}</td>
            <td>{{ customer.phone }}</td>
            <td>{{ customer.address }}</td>
          </tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import spinner from './Spinners'
import errorData from './ErrorData'

export default {
  name: "Customers",
  data() {
    return {
      customers: null,
      errored: false,
      loading: true
    }
  },
  components: {
    spinner,
    errorData
  },
  mounted() {
    axios
        .get('http://ticket_reservation.local/api/customers>',
            {
              headers: {
                'Content-type': 'application/json',
                'Accept': 'application/json'
              }
            })
        .then(response => (this.customers = response.data.data[0]))
        .catch(error => {
          console.log(error)
          this.errored = true
        })
        .finally(() => this.loading = false)
  },
}
</script>
