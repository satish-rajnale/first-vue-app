<template >
  <div>
    <v-list flat subheader>
      <v-subheader>Todos</v-subheader>

     
 
      <div v-for="task in tasks" :key="task.id">
        <v-list-item
          @click="donetasks(task.id)"
          :class="{ 'blue lighten-5': task.done }"
        >
          <template v-slot:default>
            <v-list-item-action>
              <v-checkbox :input-value="task.done"></v-checkbox>
            </v-list-item-action>

            <v-list-item-content>
              <v-list-item-title
                :class="{ 'text-decoration-line-through': task.done }"
                >{{ task.title }}</v-list-item-title
              >
              <v-list-item-subtitle
                >Notify me about updates to apps or games that I
                downloaded</v-list-item-subtitle
              >
            </v-list-item-content>
            <v-list-item-action>
              <v-btn @click.stop="deleteTask(task.id)" icon>
                <v-icon color="grey lighten-1">mdi-delete</v-icon>
              </v-btn>
            </v-list-item-action>
          </template>
        </v-list-item>
        <v-divider></v-divider>
      </div>
    </v-list>
    <v-footer
      v-bind="{fixed:true}"
      :padless="padless"
    >
     <v-text-field
        v-model="newTaskTitle"
        @click:append="addTask()"
        @keyup.enter="addTask()"
        label="Add task"
        append-icon="mdi-plus"
        class="pa-2"
        hide-details
        clearable
      ></v-text-field>
    </v-footer>

<!-- <v-card height="400px">
    <v-footer
      v-bind="{fixed:true}"
      :padless="padless"
    >
      <v-card
        flat
        tile
        width="100%"
        class="red lighten-1 text-center"
      >
      



        <v-card-text class="white--text">
          {{ new Date().getFullYear() }} — <strong>Vuetify</strong>
        </v-card-text>
      </v-card>
    </v-footer>

  
   
      
   
   
  </v-card> -->




  </div>
  
</template>

<script>
export default {
  name: "Home",
  methods: {
    donetasks(id) {
      let task = this.tasks.filter((i) => i.id === id)[0];
      task.done = !task.done;
    },
    deleteTask(id) {
      this.tasks = this.tasks.filter((i) => i.id !== id);
    },
    addTask() {
      let newTask = {
        id: Date.now(),
        title: this.newTaskTitle,
        done: false,
      };
      this.tasks.push(newTask);
      this.newTaskTitle = "";
    },
  },
  icons: [
        'mdi-home',
        'mdi-email',
        'mdi-calendar',
        'mdi-delete',
      ],
  props: [
        'default',
        'absolute',
        'fixed',
      ],
      padless: false,
      variant: 'default',
    
    computed: {
      localAttrs () {
        const attrs = {}

        if (this.variant === 'default') {
          attrs.absolute = false
          attrs.fixed = false
        } else {
          attrs[this.variant] = true
        }
        return attrs
      },
    },
  data() {
    return {
      newTaskTitle: "",
      tasks: [
        // {
        //   id: 0,
        //   title: "Todoist",
        //   done: false,
        // },
        
      ],
    };
  },
};
</script>
