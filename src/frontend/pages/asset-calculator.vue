<template>
    <v-container class="mainContainer">
        <div class="banner primary ">
            <NuxtLink to="/">
                Home
            </NuxtLink>
            <v-btn
                class="primary--text asset-btn"
                type="submit"
            >
                add asset  +
                
            </v-btn>
        </div>
        <div class="main-content">
            main content
        </div>
    </v-container>
    
    
</template>

<script>
    export default {
        auth: false,
        data(){
            return {
                
            }
        },
        methods: {

        },
    }
</script>

<style >
    .banner {
        display: inline-block;
        width: 100%;
        margin: -4% 0 0 -136px;
        height: 50px;
        border: black solid 2px; 
    }
    .asset-btn {
        align-items: center;
        margin: 0 0 0 82%;
        width: 9%;
    }

    .main-content {
        background-color: white;
        width: 1600px;
        margin: 0 0 0 -144px;
        min-height: 800px;
    }
</style>