<template>
<div>
    <div :key="task.id" v-for="task in tasks">
        <Task @toggle-remainder="$emit('toggle-remainder',task.id)" :task="task" @delete-task="$emit('delete-task',task.id)"/>
    </div>
</div>
    
</template>

<script>
import Task from './Task.vue'

export default{
    name:'Tasks',
    props:{
        tasks : Array
    },
    components:{
        Task
    },
    emits:['delete-task'],
}
</script>