<template>
    <v-form ref="form" autocomplete="off" @submit.prevent="save" >
        <v-row>
           
                    <v-col cols="12" sm="6">
                        <v-text-field
                                
                                prepend-icon="title"
                                name="title"
                                v-model="form.title"
                                :label="$t('storymapping.project.labels.title')"
                                :placeholder="$t('storymapping.project.labels.title')"
                                :error="hasInputErrors('title')"
                                :error-messages="getInputErrors('title')"
                                color="secondary"
                                :rules="required"
                        ></v-text-field>
                    </v-col>
    
 
                    <v-col cols="12" sm="6">
                        <v-text-field
                                
                                prepend-icon="description"
                                name="description"
                                v-model="form.description"
                                :label="$t('storymapping.project.labels.description')"
                                :placeholder="$t('storymapping.project.labels.description')"
                                :error="hasInputErrors('description')"
                                :error-messages="getInputErrors('description')"
                                color="secondary"
                                
                        ></v-text-field>
                    </v-col>
    
        </v-row>
    </v-form>
</template>

<script>

    import {InputErrorsByProps, RequiredRule } from '@dracul/common-frontend'
    
    
    
    

    

    export default {
        name: "ProjectForm",
        mixins: [InputErrorsByProps, RequiredRule    ],
        
        props:{
            value: {
                type: Object,
                required: true
            },
        },
        computed: {
           form: {
                get() { return this.value },
                set(val) {this.$emit('input', val)}
            }
        },
         watch: {
            form: {
                handler(newVal) {
                    this.$emit('input', newVal)
                },
                deep: true
            }
        },
        methods: {
            validate(){
              return this.$refs.form.validate()
            }
        },
        data(){
            return {
                
            }
        }
    }
</script>

<style scoped>

</style>

