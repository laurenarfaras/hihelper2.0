<template>
  <div class="hello">
    <div class="container">

      <!-- card -->
      <div v-for="offer in offers" class="demo-card-square mdl-card mdl-shadow--2dp col-xs-10 col-xs-offset-1 col-sm-5 col-sm-offset-1 col-md-4 col-lg-4">
        <div class="mdl-card__title mdl-card--expand">
          <h2 class="mdl-card__title-text">{{ offer.title }}</h2>
        </div>
        <div class="card__meta">
          <p>{{ offer.description }}</p>
          <time> ${{ offer.requestAmount }}</time>
        </div>
        <!-- <div class="mdl-card__supporting-text">
          {{ offer.description }}
        </div> -->
        <div class="mdl-card__actions mdl-card--border">
          <a class="mdl-button mdl-button--colored mdl-js-button mdl-js-ripple-effect">
            See Offer
          </a>
        </div>
      </div>

    </div>

    <div class="container-button">
      <!-- Colored FAB button with ripple -->
      <button class="mdl-button mdl-js-button mdl-button--fab mdl-js-ripple-effect mdl-button--colored">
        <router-link class="material-icons" to="/create">add</router-link>
      </button>
    </div>

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
