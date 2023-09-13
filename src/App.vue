<script setup>
    import * as Vue from 'vue';     //import Vue from 'vue';
    import 'https://demos.cloud.gooddata.com/components/ecommerce-parent-aj-jaurigue.js?auth=sso';
  //import vueCustomElement from 'vue-custom-element';
  //import { Dashboard } from 'https://demos.cloud.gooddata.com/components/ecommerce-parent-aj-jaurigue.js?auth=sso';
  //import {GoodInsight, GoodDashboard} from 'https://demos.cloud.gooddata.com/components/ecommerce-parent-aj-jaurigue.js?auth=sso';

/*  import HelloWorld from './components/HelloWorld.vue';
    import TheWelcome from './components/TheWelcome.vue'; */
//  import WebComponent from './components/WebComponentWrapper.vue';

  //Vue.use(vueCustomElement);
  //Vue.customElement('<gd-insight', Insight);
  //Vue.customElement('<gd-dashboard', Dashboard);
</script>

<template>
  <header>
    <img alt="Vue logo" class="logo" src="./assets/logo.svg" width="125" height="125" />
  </header>

  <main>
    <div class="wrapper">
      <p>First the dashboard:</p>
      <gd-dashboard dashboard="092929af-375a-4e9c-964f-2add8cdbd259"></gd-dashboard>
      <p>Then an Insight:</p>
      <gd-insight insight="f1027458-1123-4f4d-af20-0e21b1d5e009" title="Hourly Activity" style="height: 400px"></gd-insight>
    <!--   <HelloWorld msg="You did it!" /> -->
    </div>
    <!-- <TheWelcome /> -->
    <!-- <gd-insight insight="543cadbb-10b4-4153-b810-52586df7aa0e"></gd-insight> -->
    <!-- <WebComponent></WebComponent> -->
  </main>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
