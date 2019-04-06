<template>
  <v-layout row>
    <v-flex>
      <v-toolbar flat>
        <v-btn
          icon
          @click="addEntity"
        >
          <v-icon>add</v-icon>
        </v-btn>
      </v-toolbar>

      <v-container
        fluid
        grid-list-lg
      >
        <v-layout
          row
          wrap
        >
          <Entity
            v-for="entity in entities"
            :key="entity.id"
            :id="entity.id"
            @remove-entity="removeEntity"
          />
        </v-layout>
      </v-container>
    </v-flex>
  </v-layout>
</template>

<script>
import Entity from '@/components/Entity'
export default {
  name: 'Main',
  components: {
    Entity
  },
  data () {
    return {
      entityCount: 0,
      entities: []
    }
  },
  methods: {
    addEntity () {
      this.entityCount += 1
      var ent = { id: this.entityCount }
      this.entities.push(ent)
    },
    removeEntity (entity) {
      var idToRemove = entity[0]
      var arr = this.entities.filter(function (item) {
        return item.id !== idToRemove
      })
      this.entities = arr
    }
  }
}
</script>

<style>

</style>
