<template lang="pug">
  q-page.q-ma-md(padding)
    q-list(bordered separator)
      q-item(v-ripple
        :class="!task.completed ? 'bg-orange-1' : 'bg-green-1'"
        v-for="task in tasks"
        :key="task.id"
        clickable
        @click="task.completed = !task.completed")
        q-item-section(side top)
          q-checkbox(v-model="task.completed")
        q-item-section
          q-item-label(:class="{ 'text-strikethrougth': task.completed }") {{ task.name }}
        q-item-section(side top)
          .row
            q-icon(name="event" size="18px")
            .column
              q-item-label.row.justify-end(caption) {{ task.dueDate }}
              q-item-label.row.justify-end(caption): small {{ task.dueTime }}

</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  data () {
    return {
      tasks: [
        {
          id: 1,
          name: 'Go to shop',
          completed: false,
          dueDate: '2019/05/12',
          dueTime: '18:30'
        },
        {
          id: 2,
          name: 'get bananas',
          completed: false,
          dueDate: '2019/05/20',
          dueTime: '21:30'
        },
        {
          id: 3,
          name: 'Go to beach',
          completed: false,
          dueDate: '2019/05/04',
          dueTime: '18:30'
        }
      ]
    }
  }
})
</script>

<style lang="scss">
  // 終わったタスクには、削除済み線を追加する
  .text-strikethrougth {
    text-decoration: line-through;
  }
</style>
