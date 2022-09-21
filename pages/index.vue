<template>
  <main>
    <section class="bg-light">
      <div class="container d-flex flex-column align-items-center py-5">
        <h1 class="fw-bold mb-5 text-center">MANUFACTURERS</h1>
        <table>
          <tr>
            <th>NAME</th>
            <th>ESTABLISHMENT YEAR</th>
          </tr>
          <tr v-for="manufacturer in manufacturers.data">
            <td>
              {{ manufacturer.name }}
            </td>
            <td>
              {{ manufacturer.establishment_year }}
            </td>
          </tr>
        </table>
      </div>
    </section>
  </main>
</template>

<script>
export default {
  name: 'IndexPage',
  data() {
    return {
      manufacturers: [],
    }
  },
  created(){
    this.$axios.get('/api/manufacturers')
      .then((response) => {
        this.manufacturers = JSON.parse(JSON.stringify(response.data));
      })
      .catch((error) => {
        console.log(error);
      });
  }
}
</script>
