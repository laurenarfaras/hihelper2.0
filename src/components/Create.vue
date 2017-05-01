<template>
  <div class="create">
    <div class="container">
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

        <label class="mdl-checkbox mdl-js-checkbox mdl-js-ripple-effect" for="checkbox-2">
          <input type="checkbox" id="checkbox-2" class="mdl-checkbox__input">
          <span class="mdl-checkbox__label">Completed</span>
        </label>

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
  body {
    text-align: center;
  }
  .mdl-layout {
    align-items: center;
    justify-content: center;
  }
  .mdl-layout__content {
    padding: 24px;
    flex: none;
  }
  .mdl-button {
    margin-top: 10px;
    margin-bottom: 10px;
    margin-right: 10px;
  }
  .container {
    display: flex;
    justify-content: center;
  }
  .mdl-textfield {
    display: flex;
    justify-content: center;
  }
  a {
    color: #4b0082 !important;
  }
</style>
