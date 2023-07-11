<template>
  <h2>todoList</h2>
  <todoInput @addTask="addTask"></todoInput>
  <todoList :todoList="todoList"></todoList>
  <todoButton @changeActive="changeActive"></todoButton>
  
</template>

<script>
import todoList from './components/todoList.vue';
import todoButton from './components/todoButton.vue';
import todoInput from './components/todoInput.vue';
export default {
  name:"App",
  data(){
    return{
      todoList:[
        {id:1,task:'吃饭',isCompleted:true},
        {id:2,task:'睡觉',isCompleted:false},
        {id:3,task:'打豆豆',isCompleted:false},
      ],
      active:0
    }
  },
  computed:{
    todoList(){
      if(this.active===0){
        // console.log(1);
        return this.todoList;
      }
      else if(this.active===1){
        return this.todoList.filter((item)=>item.isCompleted);
      }
      else{
        return this.todoList.filter((item)=>!item.isCompleted);
      }
    }
  },
  methods:{
    changeActive(active){
      this.active=active;
      // console.log(this.active)
    },
    addTask(taskName){
      this.todoList.push({
        id:this.todoList.length+1,
        task:taskName,
        isCompleted:false,
      })
      
    }
  },
  components:{
    todoList,
    todoButton,
    todoInput
  }
}
</script>

<style>

</style>
