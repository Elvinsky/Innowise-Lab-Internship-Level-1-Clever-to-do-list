<template>
  <div v-if="user===null">
    Loading
  </div>
  <section v-else>
    <div class="header-wrapper">
      <h1 class="title">
        Taskker
      </h1>
    </div>
    <CalendarBar
      :key="componentKey"
      @change-date="handleChangeDate"
    />
    <div class="todos-wrapper">
      <TodosCollection
        :user="user"
        :day="day"
        :month="month"
        @trigger-update="handleUpdate"
      />
    </div>
    <div
      class="add-button"
      @click="openEditor"
    >
      Add Todo
    </div>
    <div
      v-if="addOpened"
      class="add-window"
      @submit.prevent
    >
      <input
        id="title"
        v-model="title"
        name="title"
        type="text"
        placeholder="Title"
      >
      <input
        id="content"
        v-model="content"
        name="title"
        type="text"
        placeholder="Content"
      >
      <input
        id="date"
        name="date"
        type="date"
        @change="onDateChange($event)"
      >
      <div>
        <button @click="addTodo">
          Add
        </button>
      </div>
    </div>
  </section>
</template>

<script>
import CalendarBar from './Calendar/CalendarBar.vue';
import TodosCollection from './Todos/TodosCollection.vue'
import { setItem } from '../scripts/dbScripts/crudApi';
export default {
    components: { CalendarBar, TodosCollection },
    data() {
        return {
            day:'14',
            month:'04',
            addOpened:false,
            title:'',
            content:'',
            timestamp:'',
            componentKey:0
        };
    },
    computed:{
        user(){
            return JSON.parse(localStorage.getItem('user'))
        }
    },
    methods:{
        handleChangeDate(time){
            this.day=new Date(time).getDate().toString();
            this.month=(new Date(time).getMonth()+1).toString();
            localStorage.setItem('timestamp',JSON.stringify(
                {
                    timestamp:time
                }
            )) 
        },
        openEditor(){
            this.addOpened=!this.addOpened
        },
        addTodo(){
            if(this.title.length===0||this.content.length===0||this.timestamp.length===0){
                return
            }
            const data={
                content:this.content,
                date:this.timestamp,
                done:false,
                name:this.title
            }
            setItem(`/users/${this.user.id}/todos`,data).then(()=>{
                this.title='',
                this.content='',
                this.timestamp='',
                this.addOpened=false
                this.handleUpdate()

            })
        },
        onDateChange(e){
            this.timestamp=e.target.valueAsNumber;
            this.handleUpdate()
        },
        handleUpdate(){
            this.componentKey+=1
        }
    }
    
}
</script>

<style scoped>
section{
    width: 580px;
    margin: auto;
    padding: 1em;

    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;

    box-shadow: 2px 2px 4px rgba(0, 0, 0, 0.405);
    border-radius: 5px;

    transition: all;
    transition-duration: 200ms;
}
.header-wrapper{
    align-self: start;
    display: flex;
    flex-direction: row;
    justify-content: space-between;
}
.todos-wrapper{
  align-self: start;
}
.add-button{
  padding: 0.4em;
  background-color: rgba(0, 255, 0, 0.527);
  border-radius: 8px;
  cursor: pointer;

  transition: all;
  transition-duration: 200ms;
}
.add-window{
  display: flex;
  flex-direction: column;
  gap: 1.3em;
  margin-top: 1.7em;
}
.add-window input{
  padding: 0.4em;
  font-size: 1em;
}
.add-window button{
  padding: 0.4em;
  background-color: rgba(0, 255, 0, 0.527);

  transition: all;
  transition-duration: 200ms;
}

.add-window button:hover{
  background-color: rgba(0, 188, 0, 0.527);
}
</style>