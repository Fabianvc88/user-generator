<template>
    <div class="identity-wrap">
      <img class="photo" v-bind:src="picture"/>
      <div class="infoTable">
        <h2 >{{firstName}} {{lastName}}</h2>
        <table>
          <tr>
            <td>Age:</td>
            <td>{{age}}</td>
          </tr>
          <tr>
            <td>Gender:</td>
            <td>{{gender}}</td>
          </tr>
          <tr>
            <td>Cellphone:</td>
            <td>{{cell}}</td>
          </tr>
          <tr>
            <td>E-mail:</td>
            <td>{{email}}</td>
          </tr>
          <tr>
            <td>Address:</td>
            <td>{{streetName}} {{streetNumber}}, {{city}}</td>
          </tr>
          <tr>
            <td></td>
            <td>{{postcode}} {{state}}</td>
          </tr>
          <tr>
            <td></td>
            <td>{{country}}</td>
          </tr>
        </table>
      </div>
      <button class="btn-generate" v-on:click="getIdentity">Generate</button>
    </div>
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
      cell: undefined,
    }
  },
  methods: {
    getIdentity() {
      fetch('https://randomuser.me/api/')
      .then(res => res.json())
      .then(jres => {
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
    .home{
    font-family: Ubuntu,sans-serif;
    text-align: center;
    background-color: #c6e5ed;
    }
    .identity-wrap{
    margin: 0em 10em;
    padding: 2em 3em;
    background-color: #fafafa;
    text-align: left;
    max-width: 70%;
    }
    .photo{
    border: 3px solid rgb(65, 65, 65);
    border-radius: 25%;
    }
    .infoTable{
    position: relative;
    left: 12em;
    top: -8.5em;
    }
    .btn-generate{
    padding: 0.6em 2em;
    border-radius: 3px;
    color: whitesmoke;
    background-color: rgb(65, 65, 65);
    }
    .btn-generate:hover{
    color: rgb(236, 236, 236);
    background-color: rgb(114, 114, 114);
    }
    table{
    font-family: arial, sans-serif;
    font-size: 15px;
    border-collapse: collapse;
    width: 50%;
    }
    td, th {
    text-align: left;
    padding: 1px;
    }
</style>