<script setup>
  import { setContext } from 'https://demos.cloud.gooddata.com/components/ecommerce-parent-dev.js'; 
  import factory, { TigerTokenAuthProvider } from "https://demos.cloud.gooddata.com/components/tigerBackend.js";

  setContext({
    backend: factory()
      .onHostname("https://____.cloud.gooddata.com")
      .withAuthentication(new TigerTokenAuthProvider("__your_token__")),
    workspaceId: "__your_workspace_id__",
  });

</script>

<template>
    <div id="content">
        <div id="left">
            <p>Left side with an Insight:</p>
            <gd-insight 
                insight="__your_visual_id__"
                title="top 10 performers" 
                style="height: 700px;"
            >
            </gd-insight>
        </div>
        <div id="right">
            <p>Right side with the dashboard:</p>
            <gd-dashboard 
                dashboard="__your_dashboard_id__"
            >
            </gd-dashboard>
        </div>
  </div>
</template>

<style scoped>
    #content {
        display: flex;
        flex-direction: row;
        flex-wrap: nowrap;
        padding: 0;
        margin:0;
    }

    #left {
        flex-direction: column;
        margin: 0 auto 2rem;
        padding: 0;
        min-width: 400px;
    }
    
    #right {
        flex-direction: column;
        margin: 0 auto 2rem;
        padding: 0;
        min-width: 700px;
    }
</style>
