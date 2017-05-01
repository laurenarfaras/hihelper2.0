<template>
  <div class="create">
    <div class="container create-container">
      <!-- <p>hi this is the create page</p> -->

      <form action="#">

        <!-- Textfield with floating label -->
        <div class="mdl-textfield mdl-js-textfield mdl-textfield--floating-label">
          <label class="mdl-textfield__label" for="sample3">Offer Title</label>
          <input class="mdl-textfield__input" type="text" id="sample3" v-model="title" required>
        </div>

        <!-- Floating Multiline Textfield -->
        <div class="mdl-textfield mdl-js-textfield mdl-textfield--floating-label">
          <label class="mdl-textfield__label" for="sample5">Offer description...</label>
          <textarea class="mdl-textfield__input" type="text" rows= "3" id="sample5" v-model="description" required></textarea>
        </div>

        <!-- Numeric Textfield with Floating Label -->
        <div class="mdl-textfield mdl-js-textfield mdl-textfield--floating-label">
          <label class="mdl-textfield__label" for="sample4">$ payment</label>
          <input class="mdl-textfield__input" type="text" pattern="-?[0-9]*(\.[0-9]+)?" id="sample4" v-model="requestAmount" required>
          <span class="mdl-textfield__error">Input is not a number!</span>
        </div>

        <!-- <label class="mdl-checkbox mdl-js-checkbox mdl-js-ripple-effect" for="checkbox-2">
          <input type="checkbox" id="checkbox-2" class="mdl-checkbox__input">
          <span class="mdl-checkbox__label">Completed</span>
        </label> -->

        <div class="container-button">
          <!-- Colored FAB button with ripple -->
          <button v-on:click="createOffer(title, description, requestAmount)" class="mdl-button mdl-js-button mdl-button--fab mdl-js-ripple-effect mdl-button--colored">
            <router-link to="/" class="material-icons md-light">done</router-link>
          </button>
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
      requestAmount: ''
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
    createOffer: function (title, description, requestAmount) {
      var url = '/offers'
      axios.post(url, {
        person: 'person',
        title: title,
        description: description,
        requestAmount: requestAmount
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
