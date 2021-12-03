<template>
    <v-container class="mainContainer">
                <NuxtLink to="/">
                    Home
                </NuxtLink>

        <div class="banner">
                <h1> Retirement Visions &amp Projections</h1>
        </div>
        <v-form id="formContainer">
            <v-container>
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
                        <v-text-field filled>$
                        </v-text-field>
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




<style>

    .mainContainer{
        background-color: white;
    }
    .banner{
        display: flexbox;
        width: 100%;
        background-color:rgba(155, 154, 156, 0.822);
        color: white;
        justify-items: center;
        align-items:center;
        height: 100px;
        margin: 0 0 1% 0;
    }

    h1{
        font-size: 44px;
        color: rgb(53, 52, 52);
        text-align: center;
        padding: 15px 0 0 0;
            }

    #formContainer{
        margin: 0 0 0 2%;
        border:black solid 2px;
        min-height: 100px;
    }

</style>