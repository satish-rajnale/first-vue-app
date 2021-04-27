<template >
  <div class="">
    <v-list flat subheader >
      <v-subheader>My daily todo</v-subheader>

      <div v-for="task in tasks" :key="task.id">
        <v-list-item @click="donetasks(task.id)" :class="{'blue lighten-5' : task.done}">
          <template v-slot:default>
            <v-list-item-action>
              <v-checkbox :input-value="task.done"></v-checkbox>
            </v-list-item-action>

            <v-list-item-content>
              <v-list-item-title>{{ task.title }}</v-list-item-title>
              <v-list-item-subtitle
                >Notify me about updates to apps or games that I
                downloaded</v-list-item-subtitle
              >
            </v-list-item-content>
          </template>
        </v-list-item>
        <v-divider></v-divider>
      </div>
    </v-list>
  </div>
</template>

<script>
export default {
  name: "Home",
  methods: {donetasks(id){
    let task = this.tasks.filter( i => i.id === id)[0];
    task.done = !task.done
  }},
  data() {
    return {
      tasks: [
        {
          id: 0,
          title: "Todoist",
          done: false,
        },
        {
          id: 1,
          title: "TickTick",
          done: false,
        },
        {
          id: 2,
          title: "Microsoft",
          done: false,
        },
        {
          id: 3,
          title: "Google Tasks",
          done: false,
        },
        {
          id: 4,
          title: "WorkFlowy",
          done: false,
        },
        {
          id: 5,
          title: "Dynalist",
          done: false,
        },
        {
          id: 6,
          title: "TaskPaper",
          done: false,
        },
        {
          id: 7,
          title: "ClickUp",
          done: false,
        },
      ],
    };
  },
};
</script>
