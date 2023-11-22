<script setup>
    import 'https://demos.cloud.gooddata.com/components/ecommerce-parent-dev.js?auth=sso'; 
</script>

<template>
    <div id="content">
        <div id="left">
            <p>Left side with an Insight:</p>
            <gd-insight 
                insight="8e8f236e-1bb2-48b3-828e-48706c684629"
                title="top 10 performers" 
                style="height: 700px;"
            >
            </gd-insight>
        </div>
        <div id="right">
            <p>Right side with the dashboard:</p>
            <gd-dashboard 
                dashboard="092929af-375a-4e9c-964f-2add8cdbd259"
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
