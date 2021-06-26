<template>
    <form @submit="onSubmit" class="add-form">
        <div class="form-control">
            <label>Task</label>
            <input type="text" v-model="text" name="text" placeholder="Add Task" />
        </div>
        <div class="form-control">
            <label >Day</label>
            <input type="text" name="day" v-model="day" placeholder="Day & Time" />
        </div>
        <div class="form-control form-control-check">
            <label >Set Remainder</label>
            <input type="checkbox" name="remainder" v-model="remainder" >
        </div>
        <input type="submit" value="Save Task" class="btn btn-block">
    </form>
</template>

<script>
export default{
    name:'AddTask',
    data(){
        return{
            text:'',
            day:'',
            remainder:false
        }
    },
    methods:{
        onSubmit(e){
            e.preventDefault()

            if(!this.text){
                alert('Enter Task')
                return
            }

            const newTask={
                text:this.text,
                day:this.day,
                remainder:this.remainder
            }

            this.$emit('add-task',newTask)

            this.text=""
            this.day=''
            this.remainder=''
        },
    }
}
</script>

<style scoped>
.add-form{
    margin-bottom: 40px;
}

.form-control{
    margin: 20px;
}
.form-control label{
    display: block;
}
.form-control input{
    width: 100%;
    padding: 3px 7px;
    margin: 5px;
    height: 40px;
    font-size: 17px;
}

.form-control-check{
    display: flex;
}

.form-control-check label{
    flex:1;
}

.form-control-check input{
    flex: 2;
    height: 20px;
}
</style>