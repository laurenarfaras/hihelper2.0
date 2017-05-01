<template>
  <div class="create">
    <div class="container create-container">
      <!-- <p>hi this is the create page</p> -->

      <form action="#">

        <!-- Textfield with floating label -->
        <div class="mdl-textfield mdl-js-textfield mdl-textfield--floating-label">
          <label class="mdl-textfield__label" for="sample3">Offer Title</label>
          <input class="mdl-textfield__input" type="text" id="sample3">
        </div>

        <!-- Floating Multiline Textfield -->
        <div class="mdl-textfield mdl-js-textfield mdl-textfield--floating-label">
          <label class="mdl-textfield__label" for="sample5">Offer description...</label>
          <textarea class="mdl-textfield__input" type="text" rows= "3" id="sample5" ></textarea>
        </div>

        <!-- Numeric Textfield with Floating Label -->
        <div class="mdl-textfield mdl-js-textfield mdl-textfield--floating-label">
          <label class="mdl-textfield__label" for="sample4">$ payment</label>
          <input class="mdl-textfield__input" type="text" pattern="-?[0-9]*(\.[0-9]+)?" id="sample4">
          <span class="mdl-textfield__error">Input is not a number!</span>
        </div>

        <!-- <label class="mdl-checkbox mdl-js-checkbox mdl-js-ripple-effect" for="checkbox-2">
          <input type="checkbox" id="checkbox-2" class="mdl-checkbox__input">
          <span class="mdl-checkbox__label">Completed</span>
        </label> -->

        <div class="container-button">
          <!-- Colored FAB button with ripple -->
          <button class="mdl-button mdl-js-button mdl-button--fab mdl-js-ripple-effect mdl-button--colored">
            <router-link to="/" class="material-icons md-light">done</router-link>
          </button>
        </div>

      </form>



    </div>
  </div>
</template>

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
