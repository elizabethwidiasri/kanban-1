<template>
  <div>
    <b-card-group deck>
      <b-card class="card_deck" header-class="card_header" :header="title" header-text-variant="white"
      >
        <draggable class="list-group" :list="list" group="people">
          <div v-for="task in list" :key="task.title">
            <Card :task="task" @delete="delTask" />
          </div>
        </draggable>
      </b-card>
    </b-card-group>
  </div>
</template>

<script>
import draggable from 'vuedraggable'
import Card from '@/components/Card'

export default {
  name: 'Cardstatus',
  components: {
    draggable,
    Card
  },
  props: ['title', 'list', 'variant'],
  methods: {
    delTask (id) {
      this.$emit('delete', id)
    }
  }
}
</script>

<style scoped>
@import url("https://fonts.googleapis.com/css?family=Montserrat|Roboto&display=swap");
@import url('https://fonts.googleapis.com/css?family=Gelasio&display=swap');

.card_header {
  border: none;
  background-color: rgb(121, 196, 167);
  font-family: 'Gelasio', serif;
  font-weight: 600;
  font-size: 20px;
  /* font-family: "Roboto", sans-serif; */
}
.card_deck {
  border: 1px rgb(139, 86, 182) solid;
}
</style>
