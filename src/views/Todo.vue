<template >
<div class="home pa-10" >
    <v-list
      flat
      subheader
      three-line
    >
      <v-subheader>My daily todo</v-subheader>

     <div  v-for="task in tasks"
          :key="task.id">
<v-list-item
         
          >
          <template v-slot:default="{ active }">
            <v-list-item-action>
              <v-checkbox :input-value="active"></v-checkbox>
            </v-list-item-action>

            <v-list-item-content>
              <v-list-item-title>{{task.title}}</v-list-item-title>
              <v-list-item-subtitle>Notify me about updates to apps or games that I downloaded</v-list-item-subtitle>
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
    name: 'Home',
    data(){
      return {
        tasks: [
          {
           id : 0,
           title: "Todoist"
          },
          {
           id : 1,
           title: "TickTick"
          },
          {
           id : 2,
           title: "Microsoft"
          },
          {
           id : 3,
           title: "Google Tasks"
          },
          {
           id : 4,
           title: "WorkFlowy"
          },
          {
           id : 5,
           title: "Dynalist"
          },
          {
           id : 6,
           title: "TaskPaper"
          },
          {
           id : 7,
           title: "ClickUp"
          }
        ]     
        }
  }
  }
</script>
