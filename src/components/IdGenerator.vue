<template>
    <v-container class="wrapper">
      <h2 class="mx-auto">Generator</h2>
      <v-card class="mt-1 mb-8" elevation="1" color="#fafafa">
        <v-card-text>
          <v-container>
            <v-row no-gutters align="center" >
              <v-col xs="12" sm="4" offset-sm="2">
                <img class="photo" v-bind:src="picture"/>
                <h2 class="mt-5">{{firstName}} {{lastName}}</h2>
              </v-col>
              <v-col xs="12" sm="4">
                <table>
                  <tr>
                    <td>Age:</td>
                    <td class="pl-5">{{age}}</td>
                  </tr>
                  <tr>
                    <td>Gender:</td>
                    <td class="pl-5">{{gender}}</td>
                  </tr>
                  <tr>
                    <td>Phone:</td>
                    <td class="pl-5">{{cell}}</td>
                  </tr>
                  <tr>
                    <td>E-mail:</td>
                    <td class="pl-5">{{email}}</td>
                  </tr>
                  <tr>
                    <td>Address:</td>
                    <td class="pl-5">{{streetNumber}} {{streetName}}</td>
                  </tr>
                  <tr>
                    <td></td>
                    <td class="pl-5">{{city}}</td>
                  </tr>
                  <tr>
                    <td></td>
                    <td class="pl-5">{{postcode}}</td>
                  </tr>
                  <tr>
                    <td></td>
                    <td class="pl-5">{{state}},{{country}}</td>
                  </tr>
                </table>
              </v-col>
            </v-row>
            <v-row>
              <v-col class="ml-1" xs="12">
                <v-btn
                  tile
                  outlined
                  color="#244F59"
                  v-on:click="getIdentity"
                >
                  <v-icon left>mdi-cog</v-icon>
                  Generate
                </v-btn>
              </v-col>
              <v-col class="mr-1" xs="12">
                <v-btn
                  class="light-blue darken-3 white--text"
                  tile
                  outlined
                >
                  <v-icon left>mdi-download</v-icon>
                  Download .csv
                </v-btn>
              </v-col>
            </v-row>
          </v-container>
        </v-card-text>
      </v-card>
    </v-container>
</template>

<script>
export default {
    data() {
    return {
      gender: 'Man',
      firstName: 'John',
      lastName: 'Doe',
      picture: 'https://randomuser.me/api/portraits/men/10.jpg',
      streetNumber: '1234',
      streetName: 'Alamosa Drive',
      city: 'Dallas',
      state: 'Texas',
      country: 'USA',
      postcode: '12345',
      email: 'johndoe@test.com',
      dob: undefined,
      age: '30',
      cell: '(123)-456-7890',
    }
  },
  methods: {
    getIdentity() {
      fetch('https://randomuser.me/api/')
      .then(res => res.json())
      .then(jres => {
        /*info = jres.results[0];*/
        this.direccion = jres.results[0].location.street.number + " " + jres.results[0].location.street.name + ", " + jres.results[0].location.city;
        this.gender = jres.results[0].gender;
        this.firstName = jres.results[0].name.first;
        this.lastName = jres.results[0].name.last;
        this.picture = jres.results[0].picture.large;
        this.streetNumber = jres.results[0].location.street.number;
        this.streetName = jres.results[0].location.street.name;
        this.city = jres.results[0].location.city;
        this.state = jres.results[0].location.state;
        this.country = jres.results[0].location.country;
        this.postcode = jres.results[0].location.postcode;
        this.email = jres.results[0].email;
        this.dob = jres.results[0].dob.date;
        this.age = jres.results[0].dob.age;
        this.cell = jres.results[0].cell;
      })
    }
  }
}
</script>

<style scoped>
    .wrapper{
    font-family: Roboto,sans-serif;
    /*background-color: #fafafa;*/
    max-width: 50em;
    }
    .photo{
    border: 1px solid rgb(65, 65, 65);
    border-radius: 4px;
    }
    /*.identity-wrap{
    margin: 0em 10em;
    padding: 2em 3em;
    background-color: #fafafa;
    text-align: left;
    max-width: 70%;
    }
    
    .infoTable{
    position: relative;
    left: 12em;
    top: -8.5em;
    }*/
    .btn-generate{
    /*padding: 0.6em 2em;
    border-radius: 3px;
    color: whitesmoke;
    background-color: rgb(65, 65, 65);*/
    }
    /*.btn-generate:hover{
    color: #D16C00;
    border-color: #D16C00;
    }*/
    table{
    font-family: arial, sans-serif;
    font-size: 14px;
    border-collapse: collapse;
    min-width: 50%;
    }
    td, th {
    text-align: left;
    padding: 1px;
    }
</style>