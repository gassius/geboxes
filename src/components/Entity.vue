<template>    
    <v-flex xs4>
    <v-card>                    
        <v-toolbar flat>
            <v-toolbar-title>{{name}}</v-toolbar-title>
            <v-spacer></v-spacer>
            <v-btn icon @click="removeEntity">
            <v-icon>remove</v-icon>
            </v-btn>
        </v-toolbar>
        <v-container fluid grid-list-sm>
            <Attribute  v-for="attribute in attributes" v-bind:key="attribute.id" :id="attribute.id" v-on:remove-attribute="removeAttribute"/>
        </v-container>
        <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn icon  @click="addAttribute">
            <v-icon>add</v-icon>
            </v-btn>
        </v-card-actions>
    </v-card>
    </v-flex>
</template>

<script>
import Attribute from '@/components/Attribute'
export default {
    name: 'entity',
    components: {
        Attribute
    },
    props: {
        id: {type: Number, required: true}
    },
    data(){
        return {
            name: 'Entity',
            attributesCount: 0,
            attributes: []       
        }
    },
    methods: {
        removeEntity() {
            this.$emit('remove-entity', [ this.id ])
        },
        addAttribute() {
            this.attributesCount+=1
            var att = {id: this.attributesCount}
            this.attributes.push(att)
        },
        removeAttribute(att) {
            var idToRemove = att[0]
            var arr = this.attributes.filter(function (item) 
            {
                return item.id != idToRemove
            })
            this.attributes = arr
        }
    }

}
</script>

<style>

</style>
