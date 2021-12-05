<template>
    <v-container class="mainContainer">
                <NuxtLink to="/">
                    Home
                </NuxtLink>

        <div class="banner">
                <h1> Retirement Visions and Projections</h1>
        </div>
        <v-form id="formContainer">
            <v-container>
                window.alert('This is sensitive information. Enter at your own risk.')
                <h2 id="formHeader">
                    Fill in your current information
                </h2>
                <v-row>
                    <v-col
                    cols="22"
                    sm="11"
                    md="3"
                    >
                        <v-text-field filled label="full name" v-model="name">name
                        </v-text-field>
                    </v-col>

                    <v-col
                    cols="22"
                    sm="11"
                    md="6"
                    >
                        <v-text-field filled label="street address">name
                        </v-text-field>
                    </v-col>

                    <v-col
                    cols="22"
                    sm="11"
                    md="1"
                    >
                        <v-text-field filled label="state">name
                        </v-text-field>
                    </v-col>

                    <v-col
                    cols="22"
                    sm="11"
                    md="2"
                    >
                        <v-text-field filled label="zipcode">name
                        </v-text-field>
                    </v-col>

                    <v-col
                    cols="22"
                    sm="11"
                    md="2"
                    >
                        <v-text-field filled label="Create Asset">
                        </v-text-field>
                    </v-col>
                    <v-col
                    cols="22"
                    sm="11"
                    md="2"
                    >
                        <v-btn 
                        type="submit" 
                        onclick="securityAlert"
                        id="submit-button" 
                        class="secondary white--text"
                        width="135"
                        >submit</v-btn>
                    </v-col>

                </v-row>
            </v-container>
            <v-text-field>

            </v-text-field>
        </v-form>
    </v-container>
    
    
</template>

<script>
    export default {
        auth: false,
        data(){
            return {
                form: {
                    name: "",
                    street: "",
                    state: "",
                    zip: "",
                }
            }
        },
        methods: {

        },
    }
</script>

<style >

    .mainContainer{
        background-color: white;
    }
    .banner{
        display: flexbox;
        width: 100%;
        background-color: var(--v-secondary-base);
        color: white;
        justify-items: center;
        align-items:center;
        height: 100px;
        margin: 0 0 1% 0;
        border-radius: 3px;
    }

  @media only screen and (max-width: 170px) {
    h1{
            font-size: 14px;
        }
    }

    h1{
        font-size: 44px;
        color: rgb(53, 52, 52);
        text-align: center;
        padding: 15px 0 0 0;
            }

    #formContainer{
        margin: 0 0 0 0;
        border:black solid 2px;
        min-height: 100px;
        background-color: var(--v-secondary-lighten3);

    }


  
</style>