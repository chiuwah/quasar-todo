<template>
  <q-page class="bg-grey-3 column">
    <q-list 
    class="bg-white"
    separator
    bordered>
      <q-item
        v-for="(task, index) in tasks"
        :key="task.title"
        @click="task.done = !task.done"
        :class="{ 'done bg-blue-1': task.done }"
        clickable
       v-ripple>
        <q-item-section avatar>
          <q-checkbox 
          v-model="task.done"
          class="no-pointer-events"
          color="primary"
           />
        </q-item-section>
        <q-item-section>
          <q-item-label>{{ task.title }}</q-item-label>
        </q-item-section>
        <q-item-section
        v-if="task.done"
        side>
          <q-btn 
          flat 
          round 
          dense
          color="primary" 
          icon="delete"
          @click.stop="deleteTask(index)" />
        </q-item-section>
      </q-item>
    </q-list>
  </q-page>
</template>

<script>
export default {
  data() {
  return {
    tasks: [
      {
     title: 'Get bananas',
     done: false 
    }, 
    {
     title: 'Eat bananas',
     done: true
    },
    {
     title: 'Poo bananas',
     done: false 
    }
    ]
  }
  },
  methods: {
    deleteTask(index) {
      this.tasks.splice(index, 1)
    }
  }
}
</script>

<style lang="scss">
.done {
  .q-item__label {
    text-decoration: line-through;
    color: #bbb;
  }
}

</style>
