<template>    
    <v-layout row>
        <v-flex grow pa-1>
            <v-card flat>
                <v-card-text @click="editingName=true">         
                    <span v-if="!editingName" >{{name}}</span>
                    <v-text-field v-if="editingName" 
                        @blur="editingName=false" 
                        v-model="name"
                        :autofocus="true" height="15px"></v-text-field>
                </v-card-text>
            </v-card>
        </v-flex>
        <v-flex shrink pa-1>
            <v-card flat>
                <v-btn icon @click="removeAttribute">
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
            editingName: false,
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
