<template>
  <div class="input-group mb-3">
    <span class="input-group-text" id="basic-addon1">新任务</span>
    <input type="text" class="form-control" placeholder="请输入任务" aria-label="Username" aria-describedby="basic-addon1" v-model="taskName">
    <button class="btn-primary" @click="onsubmit">提交</button>
  </div>
</template>

<script>
export default {
    name:"todoInput",
    data(){
        return{
            taskName:''
        }
    },
    emits:['addTask'],
    methods:{
        onsubmit(){
            this.$emit('addTask',this.taskName),
            this.taskName=''
        }
    }
}
</script>

<style scoped>
.input-group{
    width: 500px;
    margin:0 auto;
}
</style>