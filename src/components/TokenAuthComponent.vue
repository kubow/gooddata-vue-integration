<script setup>
  import { onMounted } from 'vue';

    onMounted(async () => {
        // Construct the first module URL using environment variables
        const wsUrl = `${import.meta.env.VITE_HOST}components/${import.meta.env.VITE_WORKSPACE}.js`;
        const beUrl = `${import.meta.env.VITE_HOST}components/tigerBackend.js`

        try {
            // Dynamically import the modules using the constructed URL and static URL
            const { setContext } = await import(/* @vite-ignore */ wsUrl);
            const { default: factory, TigerTokenAuthProvider } = await import(/* @vite-ignore */ beUrl);
            console.log("Imported well, no error above?, now settings context")

            // Use the imported functions to set the context
            setContext({
            backend: factory()
                .onHostname(import.meta.env.VITE_HOST) // Use env variable for hostname
                .withAuthentication(new TigerTokenAuthProvider(import.meta.env.VITE_TOKEN)), // Use env variable for token
            workspaceId: import.meta.env.VITE_WORKSPACE, // Use env variable for workspace ID
            });
            console.log("Also succesull, now using components...")
        } catch (error) {
            console.error('Error loading modules:', error);
        }
    });

    const dashboardId = import.meta.env.VITE_DASHBOARD;
    const visualId = import.meta.env.VITE_VISUALIZATION;
    console.log(`${dashboardId} / ${visualId}`);

</script>

<template>
    <div id="content">
        <div id="left">
            <p>Left side with an Insight:</p>
            <gd-insight 
                :insight="visualId"
                title="top 10 performers" 
                style="height: 700px;"
            >
            </gd-insight>
        </div>
        <div id="right">
            <p>Right side with the dashboard:</p>
            <gd-dashboard 
                :dashboard="dashboardId"
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
