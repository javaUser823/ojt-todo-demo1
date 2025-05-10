<template>
  <v-container>
    <!-- one way binding -->
     <h2>{{ title }} </h2>
     <!-- two way binding -->
     <v-text-field label="Enter your name : " v-model="name"></v-text-field>
      Hello : {{ name }}
  </v-container>
</template>

<script>

export default {
  name: 'HelloWorld',

  data: () => ({
   title:"This is my first vue project.",
   name:""
  }),
}
</script>
