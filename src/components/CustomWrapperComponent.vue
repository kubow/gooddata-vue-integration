<template>
    <div>
      <!-- ...Your other Vue.js components here... -->
        Here
      <!-- Placeholder for the web components -->
      <div ref="webComponentsContainer"></div>
    </div>
  </template>
  
  <script>
  
  // Custom element: https://github.com/karol-f/vue-custom-element
  // or a more sophisticated way  
  export default {
    mounted() {
      // Load the web component script dynamically
      const script = document.createElement('script');
      script.src = 'https://demos.cloud.gooddata.com/components/ecommerce-parent-aj-jaurigue.js?auth=sso';
      script.defer = true;
      script.onload = this.initializeWebComponents;
      document.body.appendChild(script);
    },
    methods: {
      initializeWebComponents() {
        // Assuming the web components are globally registered by the script
        // Access the web components using their tag names
        const gdDashboard = document.createElement('gd-dashboard');
        gdDashboard.setAttribute('dashboard', '092929af-375a-4e9c-964f-2add8cdbd259');
        gdDashboard.style.height = '700px';
        gdDashboard.style.width = '1024px';
  
        const gdInsight = document.createElement('gd-insight');
        gdInsight.setAttribute('insight', '543cadbb-10b4-4153-b810-52586df7aa0e');
        gdInsight.setAttribute('workspace', '4248');
        gdInsight.setAttribute('locale', 'en_US');
        gdInsight.setAttribute('title', 'Custom insight title');
  
        // Append the web components to the container element
        const container = this.$refs.webComponentsContainer;
        container.appendChild(gdDashboard);
        container.appendChild(gdInsight);
      },
    },
  };
      
      // another alternative
      //import vueCustomElement from 'vue-custom-element';
      //import {GoodInsight, GoodDashboard} from 'https://demos.cloud.gooddata.com/components/ecommerce-parent-aj-jaurigue.js?auth=sso';
      //Vue.use(vueCustomElement);
      //Vue.customElement('<gd-insight', Insight);
      //Vue.customElement('<gd-dashboard', Dashboard);
  </script>
