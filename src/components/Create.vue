<template>
  <div class="create">
    <div class="container create-container">
      <!-- <p>hi this is the create page</p> -->

      <form action="#">

        <!-- Textfield with floating label -->
        <div class="mdl-textfield mdl-js-textfield mdl-textfield--floating-label">
          <!-- <label class="mdl-textfield__label" for="sample3">Offer Title</label> -->
          <input placeholder="offer title" class="mdl-textfield__input" type="text" id="offer-title" v-model="title" required>
        </div>

        <!-- Floating Multiline Textfield -->
        <div class="mdl-textfield mdl-js-textfield mdl-textfield--floating-label">
          <!-- <label class="mdl-textfield__label" for="sample5">Offer description...</label> -->
          <textarea placeholder="offer description..." class="mdl-textfield__input" type="text" rows= "3" id="offer-description" v-model="description" required></textarea>
        </div>

        <!-- Numeric Textfield with Floating Label -->
        <div class="mdl-textfield mdl-js-textfield mdl-textfield--floating-label">
          <!-- <label class="mdl-textfield__label" for="sample4">$ payment</label> -->
          <input placeholder="$ payment" class="mdl-textfield__input" type="text" pattern="-?[0-9]*(\.[0-9]+)?" id="payment" v-model="requestAmount" required>
          <span class="mdl-textfield__error">Input is not a number!</span>
        </div>

        <div class="mdl-textfield mdl-js-textfield mdl-textfield--floating-label">
          <input placeholder="your name" class="mdl-textfield__input" type="text" id="offer-person" v-model="person" required>
        </div>

        <div class="mdl-textfield mdl-js-textfield mdl-textfield--floating-label">
          <input placeholder="email" class="mdl-textfield__input" type="text" id="offer-email" v-model="email" required>
        </div>

        <!-- <label class="mdl-checkbox mdl-js-checkbox mdl-js-ripple-effect" for="checkbox-2">
          <input type="checkbox" id="checkbox-2" class="mdl-checkbox__input">
          <span class="mdl-checkbox__label">Completed</span>
        </label> -->

        <div class="container-button">
          <!-- Colored FAB button with ripple -->
          <router-link to="/">
            <button v-on:click="createOffer(title, description, requestAmount, person, email)" class="mdl-button mdl-js-button mdl-button--fab mdl-js-ripple-effect mdl-button--colored">
              <i class="material-icons md-light">done</i>
            </button>
          </router-link>
        </div>

      </form>



    </div>
  </div>
</template>

<script>
export default {
  name: 'create',
  data () {
    return {
      offers: [],
      person: '',
      title: '',
      description: '',
      requestAmount: '',
      email: ''
    }
  },
  methods: {
    getDashboardOffers: function () {
      var url = '/offers'
      axios.get(url)
          .then(function (response) {
            this.offers = response.data.offers
          }.bind(this))
          .catch(function (err) {
            console.log(err)
          })
    },
    createOffer: function (title, description, requestAmount, person, email) {
      var url = '/offers'
      axios.post(url, {
        person: person,
        title: title,
        description: description,
        requestAmount: requestAmount,
        email: email
      })
      .then(function (response) {
        console.log("posted successfully");
      })
      .catch(function (err) {
        console.log(err);
      })

      this.getDashboardOffers()

    }
  },
  created: function () {

  }
}

// Performing a POST request
// axios.post('/save', { firstName: 'Marlon', lastName: 'Bernardes' })
//   .then(function(response){
//     console.log('saved successfully')
//   });

</script>


<style>
  a {
    color: #4b0082 !important;
  }
  .create-container {
    display: flex;
    justify-content: center;
    align-items: center;
  }
  .mdl-textfield {
    display: flex;
    justify-content: center;
  }
</style>
