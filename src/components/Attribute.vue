<template>    
    <v-layout row>
        <v-flex grow pa-1>
            <v-card flat>
                <v-card-text>         
                    Attribute
                </v-card-text>
            </v-card>
        </v-flex>
        <v-flex shrink pa-1>
            <v-card flat>
                <v-btn icon>
                <v-icon>remove</v-icon>
                </v-btn>
            </v-card>
        </v-flex>
    </v-layout>
</template>

<script>
export default {
    name: 'attribute',
    props: {
        id: {type: Number, required: true}
    },
    data(){
        return {
            name: 'Attribute'  
        }
    },
    methods: {
        removeAttribute() {
            this.$emit('remove-attribute', [ this.id ])
        }
    }
}
</script>

<style>

</style>
