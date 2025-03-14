<script setup>
    import { onMounted, onBeforeUnmount } from 'vue';
    // Construct the URL using environment variables
    const dashboardUrl = `${import.meta.env.VITE_HOST}dashboards/embedded/#/workspace/${import.meta.env.VITE_WORKSPACE}/dashboard/${import.meta.env.VITE_DASHBOARD}?showNavigation=false&setHeight=700`;
    const visualUrl = `${import.meta.env.VITE_HOST}analyze/embedded/#/${import.meta.env.VITE_WORKSPACE}/${import.meta.env.VITE_VISUALIZATION}`;
    console.log(`loading iframe dashboard from ${dashboardUrl} \n loading iframe visual builder from ${visualUrl}}`);


    // Function to handle window events, like messages from the iframe
    function handleWindowMessage(event) {
        console.log('Message received from iframe:', event.data);
    }

    onMounted(() => {
        // Add the event listener when the component is mounted
        window.addEventListener('message', handleWindowMessage);
    });

    onBeforeUnmount(() => {
        // Clean up the event listener when the component is destroyed
        window.removeEventListener('message', handleWindowMessage);
    });
</script>

<template>
    <div id="content">
        <div id="left">
            <p>Left side with an Insight:</p>
            <iframe 
                id="embedded-insight"
                :src="visualUrl" 
                height="700px" 
                width="100%" 
                frameborder="0"
                @insightLoaded="handleInsight"
                >
            </iframe>
        </div>
        <div id="right">
            <p>Right side with the dashboard:</p>
            <iframe 
                id="embedded-dashboard"
                :src="dashboardUrl" 
                height="700px" 
                width="100%" 
                frameborder="0"
                @dashboardLoaded="handleDashboard"
                >
            </iframe>
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
