<template>
    <v-row class="mt-4">
        <v-col cols="6" class="mx-auto">
            <v-card elevation="1">
                <v-img
                    src="https://cdn.vuetifyjs.com/images/cards/sunshine.jpg"
                    height="100px"
                ></v-img>
                <v-row class="mx-12">
                    <v-col class="mx-12">
                        <v-row class="pt-4">
                            <v-col>
                                <span class="title">OCR Upload Page</span>
                            </v-col>
                        </v-row>
                        <v-row>
                            <v-col cols="9">
                                <v-file-input
                                    truncate-length="15"
                                    @change="selectFile"
                                    label="Text available image"
                                ></v-file-input>
                            </v-col>
                            <v-col class="pt-6">
                                <v-btn 
                                    v-on:click="submitFile()"
                                    >Submit
                                </v-btn>
                            </v-col>
                        </v-row>
                        <template v-if="resulttext">
                            <v-row>
                                <v-col>
                                    OCR Result
                                    <v-textarea
                                        solo
                                        readonly
                                        name="input-7-4"
                                        :value="resulttext"
                                    ></v-textarea>
                                </v-col>
                            </v-row>
                        </template>
                    </v-col>
                </v-row>
            </v-card>
        </v-col>
    </v-row>
</template>

<script>

export default {
    data : function () { 
        return { 
            file: '',
            currentFile: undefined,
            message: "",
            resulttext: null,
            

        }
    }, 
    methods : { 
        handleFileUpload(){
            this.file = this.$refs.file.files[0];
        },
        submitFile(){
            var baseURI = "http://127.0.0.1:4000/api/v1/"; 

            if (!this.currentFile) {
                this.message = "Please select a file!";
                return;
            }

            let formData = new FormData();
            formData.append('file', this.currentFile);

            this.$http.post( baseURI+'store-file',
                formData,
                {
                    headers: {
                        'Content-Type': 'multipart/form-data'
                    }
                }
                ).then((r) => {
                    if (r.data.status == "success") { 
                        this.resulttext = r.data.text;
                    }
                })
                .catch(function(){
                    console.log('FAILURE!!');
                });
        },
        selectFile(file) {
            this.currentFile = file;
        },
    }, 
}
</script>
