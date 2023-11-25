  <script>
   // step 1: introduce in package.json
   // "@gooddata/sdk-backend-tiger": "^9.4.0",
   // "@gooddata/sdk-model": "^9.4.0",
   // "@gooddata/sdk-ui": "^9.4.0",
   // "@gooddata/sdk-ui-dashboard": "^9.4.0",
   // "veaury": "^2.3.12",
   
   // step 2: follow same as in https://github.com/gooddata/ui-sdk-examples/tree/master/vue-project
   import React from 'react';
   import App from './reactApp';
   import { render } from 'react-dom';

   export default {
    props: ['data'],
    mounted() {
      
    const container = document.getElementById('app2');
    render(<App />, container);

    },
    beforeDestroy() {
      // Clean up the React component when the Vue component is destroyed
      ReactDOM.unmountComponentAtNode(this.$refs.reactContainer);
    },
  };
  </script>

<template>
  <div>
    <!-- ...Your other Vue.js components here... -->
      Here
    <!-- Step 3. introduce the custom JSX component (React) -->
    <div ref="webComponentsContainer"></div>
  </div>
</template>