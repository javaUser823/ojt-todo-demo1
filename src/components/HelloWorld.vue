<template>
  <v-container>
    <!-- one way binding -->
     <h2>{{ title }} </h2>
     <v-row>
      <v-col cols="12">
        <div>
          <v-text-field label="Enter your name : " v-model="name" @keydown.enter="changeFlag" :disabled="flag"></v-text-field >
          Hello : {{ name }}
        </div>
      </v-col>
     </v-row>
     <!-- two way binding -->
     <v-row>
      <v-col cols="9">
        <v-text-field label="WHAT WILL YOU DO" v-model="todo"></v-text-field>
      </v-col>
      <v-col cols="3">
        <v-text-field label="HOW LONG IT WILL TAKE" v-model="duration"></v-text-field>
      </v-col>
     </v-row>
      <v-row>
        <v-col cols="2">
          <div>
            <v-btn @click="add">
            Add To Do List
            </v-btn>
          </div>
        </v-col>
        <v-col cols="1">
          <div>
            <v-btn @click="de">
            DELETE
            </v-btn>
          </div>
        </v-col>
      </v-row>
      <v-row>
        
      </v-row>
      <div>
         <v-table theme="dark">
    <thead>
      <tr>
        <th class="text-left">
          NO
        </th>
        <th class="text-left">
          TODO
        </th>
        <th class="text-left">
          DURATION
        </th>
      </tr>
    </thead>
    <tbody>
      <tr
        v-for="item in todolist"
        :key="item.todo"
      >
        <td>{{ item.id }}</td>
        <td>{{ item.todo }}</td>
        <td>{{ item.duration }} hr(s)</td>
      </tr>
    </tbody>
  </v-table>
      </div>
  </v-container>
</template>

<script>

export default {
  name: 'HelloWorld',

  data: () => ({
   title:"This is my first vue project.",
   name:"",
   flag:false,
   todo:"",
   duration:"",
   selectedId: null,

    todolist:[
    {
      id:1,
      todo: 'Attend To OJT Class',
      duration: 3,
    },
    {
      id:2,
      todo: 'Clean the House',
      duration: 0.5,
    },
  ]

  }),

  methods:{
    add(){
      this.todolist.push({id:this.todolist.length+1, todo:this.todo, duration:this.duration}),
      this.todo="",
      this.duration=""
    },
    changeFlag(){
      this.flag=!this.flag
    },
    de(){
      this.todolist.pop()
    },
    update(){
    }
  }

}
</script>
