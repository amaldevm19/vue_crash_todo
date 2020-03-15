<template>
    <div>
        <form @submit="addtodo">
            <input type="text" name="title" placeholder="Add Todo..." v-model="title">
            <input type="submit" value="Submit" class="btn">
        </form>
    </div>
</template>
<script>
    import { v4 as uuidv4 } from 'uuid'
    export default {
        name:"Addtodo",
        data(){
           return{ title:""}
        },
        methods:{
            addtodo(e){
                e.preventDefault();
                const newTodo = {
                    id: uuidv4(),
                    title: this.title,
                    completed:false
                }
                this.$emit('add-todo', newTodo);
                this.title='';
                
            }
        }
    }
 
</script>
<style scoped>
    form{
        display:flex;
    }
    input[type='text']{
        flex: 10;
        padding: 5px;
    }
    input[type='submit']{
        flex: 2;
    }
    .btn{
        display: inline-block;
        border: none;
        background: #555;
        color:#fff;
        padding:7px 20px;
        cursor: pointer;

    }
    .btn:hover{
        background: #777;
    }
</style>

