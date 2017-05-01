<template>
  <div class="hello">
    <div class="container-fluid">

      <div class="row">
        <!-- card -->
        <div v-for="(offer, index) in offers" class="demo-card-square mdl-card mdl-shadow--2dp col-xs-10 col-xs-offset-1 col-sm-5 col-sm-offset-1 col-md-3 col-md-offset-2 col-lg-3 col-lg-offset-2">
          <div class="mdl-card__title mdl-card--expand">
            <h2 class="title-text mdl-card__title-text">{{ offer.title }}</h2>
          </div>
          <div class="card__meta">
            <p class="offer-description">{{ offer.description }}</p>
            <time> ${{ offer.requestAmount }}</time>
          </div>
          <!-- <div class="mdl-card__supporting-text">
            {{ offer.description }}
          </div> -->
          <div class="mdl-card__actions mdl-card--border">
            <button v-on:click="seeOffer(offer, index)" type="button" class="offer-button mdl-button" :key="index">
              See Offer
            </button>
            <!-- <a class="mdl-button mdl-button--colored mdl-js-button mdl-js-ripple-effect">
              See Offer
            </a> -->
      </div>


        </div>
      </div>

    </div>

    <div class="container-button">
      <!-- Colored FAB button with ripple -->
      <router-link to="/create">
        <button class="mdl-button mdl-js-button mdl-button--fab mdl-js-ripple-effect mdl-button--colored">
          <i class="material-icons">add</i>
        </button>
      </router-link>
    </div>


    <dialog class="mdl-dialog">
      <h4 class="mdl-dialog__title" id="mdl-title">Allow data collection?</h4>
      <div class="mdl-dialog__content">
        <p id="mdl-description"></p>
        <p id="mdl-payment"></p>
        <p id="mdl-person"></p>
      </div>
      <div class="mdl-dialog__actions">
        <a type="button" id="mail-contact" class="mdl-button" href="">Contact</a>
        <button type="button" class="mdl-button close">Close</button>
      </div>
    </dialog>

  </div>
</template>

<script>
export default {
  name: 'hello',
  data () {
    return {
      offers: []
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
    seeOffer: function (offer, index) {
      var url = `/offers/${offer._id}`
      axios.get(url)
          .then(function (response) {
            var dialog = document.querySelector('dialog');
            var rd = response.data.offers[0]
            document.querySelector('#mdl-title').innerText = rd.title
            document.querySelector('#mdl-description').innerText = rd.description
            document.querySelector('#mdl-payment').innerText = "$" + rd.requestAmount
            document.querySelector('#mdl-person').innerText = "posted by: " + rd.person + "\n on " + rd.updated.slice(0,10)
            document.querySelector('#mail-contact').href = "mailto:" + rd.email
            // document.querySelector('#mdl-date').innerText = rd.updated.slice(0,10)
            //var showDialogButton = document.querySelector('');

            if (! dialog.showModal) {
              dialogPolyfill.registerDialog(dialog);
            }
            dialog.showModal();
            dialog.querySelector('.close').addEventListener('click', function() {
              dialog.close();
            });
          }.bind(this))
          .catch(function (err) {
            console.log(err);
          })
    }
  },
  created: function () {
    this.getDashboardOffers()
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}

.container-fluid {
  display: flex;
  justify-content: center;
}

div .row {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}

.mdl-button {
  color: darkslategray;
}

.mdl-card__actions {
  background-color: lavender !important;
}

time {
  margin-left: 1em;
  padding-left: 1em;
}

.offer-description {
  text-align: left;
}

.title-text {
  text-align: center;
}

div.mdl-card__title.mdl-card--expand {
  justify-content: center;
}

/*.container-button {
  display: block;
  margin: 0.8em;
}*/

.container-button button {
  position: fixed;
  left: 80%;
  top: 80%;
  z-index: 2;
}

.demo-card-square.mdl-card {
  /*width: 320px;
  height: 320px;*/
  margin: 0.5em;
}

.mdl-card__title-text {
  align-self: flex-start;
}

/* card meta */
    .card__meta {
        margin-top: 0.5em;
        /*font-size: 1.5rem;*/
        color: #656565;
        margin-left: 0.8rem;
        margin-right: 0.8rem;
        display: flex;
        justify-content: space-between;
    }

.col-xs-10, .col-sm-5, .col-md-3, .col-lg-3 {
  padding-left: 0% !important;
  padding-right: 0% !important;
}
</style>
