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
            <v-btn @click="add" prepend-icon="mdi-plus">
            Add To Do List
            </v-btn>
          </div>
        </v-col>
        <v-col cols="2">
        </v-col>
      </v-row>
      <v-row>
        
      </v-row>
      <div>
         <v-table>
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
        <th class="text-left">
          REMARK
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
        <td v-if="item.duration > 0.75 ">Lazy</td>
        <td v-else>Active</td>
        <td><v-btn @click="removeItem(item)" prepend-icon="mdi-delete-variant">REMOVE</v-btn></td>
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
    generateId(){
      return this.todolist[this.todolist.length-1].id+1
    },
    add(){
      this.todolist.push({id:this.generateId(), todo:this.todo, duration:this.duration}),
      this.todo="",
      this.duration=""
    },
    changeFlag(){
      this.flag=!this.flag
    },
    removeItem(item){
      this.todolist=this.todolist.filter(todo => todo.todo != item.todo)
    },
  async remove(){
   console.log("one")
      await new Promise(resolve =>
     setTimeout(()=>{
      console.log("two"); resolve();
     },5000)
     )      
      console.log("three")
  }
  },
 async created(){
      await new Promise(resolve =>
     setTimeout(()=>{this.title="This is my first vue project !!!"; resolve();
     },5000)
     )      
    
  }

}
</script>
