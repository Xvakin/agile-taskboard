<template>
     <div class="archive">
        <div class="archive-container">
            <button class="btn-close-arch" @click="$emit('closeArchive')">Close</button> 
            <div class="archive-header">{{archive.name}}</div>
            <div class="archive-section">
                <div class="tasks-container">
                    <Task v-bind:task="task" v-bind:index="index" v-bind:key="index" v-for="(task, index) in archive.tasks">
                    </Task>
                </div>
                <div class="task-category-container">
                    <!-- <TaskCategory  v-for="category in categories" v-bind:key="category.id" v-bind:tasks="tasks" v-bind:category="category" >
                    </TaskCategory> -->
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import Task from "./task.vue";
// import TaskCategory from './components/task-category.vue';

export default {
    name: "Archive",
    props: ["tasks", "task","index", "closeArchive", "categories", "category"],
    inject: ["archive"],
    components: {
      Task
    },
    provide: function() {
    return {
      tasks: this.archive.tasks
    }
  },
    methods: {
        showArchiveInfo() {
        this.showArchive = true;
        },
    }
}
</script>

<style scoped>
 .archive {
        /* display: none; */
    position: fixed;
    display:flex;
    justify-content:center;
    align-items:center;
    top:0;
    right:0;
    left:0;
    bottom:0;
    background-color:rgb(133, 108, 108, 0.5)
}

.archive-container {
    position: relative;
    display: flex;
    flex-wrap: wrap;
    flex-direction:column;
    width: 1040px;
    height: 630px;
    background-color: white;
    border: 1px solid rgb(221, 221, 221);
    border-radius: 10px;
}

.archive-header {
    font-family: 'Work Sans', sans-serif;
    color: rgb(82, 81, 81);
    font-size: 20px;
    text-align: center;
    margin: 10px auto;
    height: 30px;
    border: 1px solid rgb(255, 255, 255);
    border-radius: 6px;
    background-color: rgb(255, 254, 254) ;
    box-shadow: 0px -1px 26px -11px rgba(0,0,0,0.75);
    -webkit-box-shadow: 0px -1px 26px -11px rgba(0,0,0,0.75);
    -moz-box-shadow: 0px -1px 26px -11px rgba(0,0,0,0.75);
    width: 70%;
    padding: 10px;
}

.archive-section {
    position: absolute;
    margin-top: 70px;
    width: 1000px;
    height: 530px;
    display: flex;
}

.archive-section > .tasks-container {
    width: 300px;
    margin: 20px;
    display: flex;
    flex-wrap: wrap;
    flex-direction: column;
}

.tasks-container > .tasks {
    width: 300px;
    margin: 20px;
}


.btn-close-arch {
    position: absolute;
    font-size: 10px;
    width: 100px;
    height: 30px;
    right: 10px;
    top: 10px;
    font-family: 'Work Sans', sans-serif;
    border: none;
    border-radius: 10px;
    box-shadow: 0px -1px 26px -11px rgba(0,0,0,0.75);
    -webkit-box-shadow: 0px -1px 26px -11px rgba(0,0,0,0.75);
    -moz-box-shadow: 0px -1px 26px -11px rgba(0,0,0,0.75);
    background-color: white;
    color: rgb(126, 125, 125);
    cursor: pointer;
}

</style>