<script setup>
    import { onMounted } from 'vue';

    onMounted(() => {
        // Construct the URL using environment variables
        const scriptUrl = `${import.meta.env.VITE_HOST}components/${import.meta.env.VITE_WORKSPACE}.js?auth=sso`;
        console.log(scriptUrl);
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
                insight={{import.meta.env.VITE_VISUALIZATION}}
                title="top 10 performers" 
                style="height: 700px;"
            >
            </gd-insight>
        </div>
        <div id="right">
            <p>Right side with the dashboard:</p>
            <gd-dashboard 
                dashboard={{import.meta.env.VITE_DASHBOARD}}
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
