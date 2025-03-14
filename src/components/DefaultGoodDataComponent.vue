<script setup>
    import { onMounted } from 'vue';
    // Construct the URL using environment variables
    const scriptUrl = `${import.meta.env.VITE_HOST}components/${import.meta.env.VITE_WORKSPACE}.js?auth=sso`;
    const dashboardId = import.meta.env.VITE_DASHBOARD;
    const visualId = import.meta.env.VITE_VISUALIZATION;
    console.log(`loading web components from ${scriptUrl} \n dashboard id ${dashboardId} \n visual id ${visualId}}`);

    // Define event handlers for insight and dashboard events
    function handleInsight(event) {
    console.log('Insight loaded:', event);
    }

    function handleDashboard(event) {
    console.log('Dashboard loaded:', event);
    }

    onMounted(() => {
        // Check if the script is already loaded to prevent adding it multiple times
        if (!document.querySelector(`script[src="${scriptUrl}"]`)) {
            // Dynamically create and add the script tag
            const script = document.createElement('script');
            script.src = scriptUrl;
            script.type = 'module'; // Use 'module' for ES modules
            document.head.appendChild(script);
        }
    });

</script>

<template>
    <div id="content">
        <div id="left">
            <p>Left side with an Insight:</p>
            <gd-insight 
                :insight="visualId"
                title="top 10 performers" 
                style="height: 700px;"
                @insightLoaded="handleInsight"
            >
            </gd-insight>
        </div>
        <div id="right">
            <p>Right side with the dashboard:</p>
            <gd-dashboard 
                :dashboard="dashboardId"
                @dashboardLoaded="handleDashboard"
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
        margin: 0;
    }

    #left {
        flex-direction: column;
        margin: 0 auto 2rem;
        padding: 1%;
        min-width: 400px;
    }
    
    #right {
        flex-direction: column;
        margin: 0 auto 2rem;
        padding: 1%;
        min-width: 700px;
    }
</style>
