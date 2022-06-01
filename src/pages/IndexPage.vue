<template>
  <q-page class="flex flex-center">
     <q-card class="my-card">
       <q-seperator>
         <!-- first part -->
         <q-card-section>
           <div class="text-h4 text-center" style="width:600px">
             To-Do List
           </div>
         </q-card-section>
         <q-card-section>
           <div class="row justify-center">
             <div class="col-12">
               <q-input v-model="todoTask" label="Input Task">
   <template v-slot:after>
   <q-btn round dense flat icon="send" @click="addItem"></q-btn>
   </template>
               </q-input>

             </div>
           </div>
         </q-card-section>

       </q-seperator>
       <!-- second part -->
      <q-card-section v-if="todoList.length">
        <div class="row justify-center" v-for="(item, index) in todoList" :key="index">
          <div class="col-8 q-py-md">
            {{item.value}}
          </div>
          <div class="col-auto q-py-md">
          <q-btn  dense flat icon="done" @click="removeItem(index)"></q-btn>
</div>
        </div>
      </q-card-section>
      <!-- third part -->
      <q-card-selection v-else>
<div class="col-12 q-py-lg">
  <div class="text-h6 text-center">
    No Items in the list
  </div>
</div>
      </q-card-selection>
    </q-card>
  </q-page>
</template>

<script>
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'IndexPage',
  data () {
    return {
      todoTask: '',
      todoList: [
        {
          value: 'create an app'
        },
        {
          value: 'Build an app'
        }
      ]
    }
  },
  methods: {
    addItem () {
      this.todoList.push({ value: this.todoTask })
    },
    removeItem (index) {
      this.todoList.splice(index, 1)
    }
  }
})
</script>
