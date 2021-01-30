<template>
    <v-row>
        <v-col class="mx-auto mt-8" cols="3">
            <v-card elevation="1" class="mx-4">
                <v-img
                src="https://cdn.vuetifyjs.com/images/cards/sunshine.jpg"
                height="200px"
                ></v-img>

                <v-card-title>Github Repo Link</v-card-title>
                <template>
                    <v-btn color="orange lighten-2" target="_blank" text href="https://github.com/mengfong96/ocr-laravel-api">Ocr Laravel API</v-btn>
                    <v-btn color="orange lighten-2" target="_blank" text href="https://github.com/mengfong96/ocr-laravel-ui">Ocr Laravel UI</v-btn>
                </template>

                <v-card-title>OCR Text Converting</v-card-title>
                <v-card-text>
                    This is a initiative to implement Tesseract OCR in Vuejs and Laravel framework with the SPA style. 
                </v-card-text>
                <v-card-actions>
                    <v-btn
                        color="orange lighten-2"
                        text
                        @click="$router.push('ocr-upload')"
                    >
                        Go!
                    </v-btn>
                    <v-spacer></v-spacer>
                </v-card-actions>
            </v-card>
        </v-col>
    </v-row>
</template>

<script>
export default {
    data: function() {
        return{ 
            
        }
    },
    components: {

    },
    methods: { 
        
    }
}
</script>
