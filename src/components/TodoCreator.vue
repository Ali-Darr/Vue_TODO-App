<script setup>

import { reactive } from "vue";
import TodoButton from './TodoButton.vue'

const emit = defineEmits(["create-todo"]);

const todoState = reactive({
    taskName: "",
    taskerMail: "",
    taskTime: "",
    isFieldInvalid: [false, false, false],
    errMsg: ["Task Name", "Tasker Mail", "Task Time"],
})


const createTodo = () => {

    todoState.isFieldInvalid.fill(false);

    if (todoState.taskName !== "" && todoState.taskerMail !== "" && todoState.taskTime !== "") {

        emit("create-todo", todoState.taskName, todoState.taskerMail, todoState.taskTime);

        todoState.taskName = "";
        todoState.taskerMail = "";
        todoState.taskTime = "";

        return;
    }

    if (todoState.taskName === "") {
        todoState.isFieldInvalid[0] = true;
    }
    if (todoState.taskerMail === "") {
        todoState.isFieldInvalid[1] = true;
    }
    if (todoState.taskTime === "") {
        todoState.isFieldInvalid[2] = true;
    }
}

</script>

<template>
    <div class="container mt-5">
        <div class="row justify-content-center">

            <div class="col-md-4 col-12">
                <div class="input-group mb-3">
                    <input type="text" class="form-control border border-primary"
                        :class="{ 'border-danger': todoState.isFieldInvalid[0] }" placeholder="Enter Task Name"
                        v-model="todoState.taskName" aria-label="Enter Task Name" aria-describedby="button-addon2">
                </div>
                <p class="mb-3 errMsg" v-show="todoState.isFieldInvalid[0]">{{ todoState.errMsg[0] }} cannot be empty</p>
            </div>

            <div class="col-md-4 col-12">
                <div class="input-group mb-3">
                    <input type="text" class="form-control border border-primary"
                        :class="{ 'border-danger': todoState.isFieldInvalid[1] }" placeholder="Enter Tasker Email"
                        v-model="todoState.taskerMail" aria-label="Enter Tasker Email" aria-describedby="button-addon2">
                </div>
                <p class="mb-3 errMsg" v-show="todoState.isFieldInvalid[1]">{{ todoState.errMsg[1] }}
                    cannot be
                    empty</p>
            </div>

            <div class="col-md-3 col-12">
                <div class="input-group mb-3">
                    <input type="text" class="form-control border border-primary"
                        :class="{ 'border-danger': todoState.isFieldInvalid[2] }" placeholder="Enter Task Time"
                        v-model="todoState.taskTime" aria-label="Enter Task Time" aria-describedby="button-addon2">
                </div>
                <p class="mb-3 errMsg" v-show="todoState.isFieldInvalid[2]">{{ todoState.errMsg[2] }} cannot be empty</p>
            </div>

            <div class="col-md-1 col-12">
                <TodoButton @click="createTodo()" />
            </div>

        </div>
    </div>
</template>

<style scoped>
.errMsg {
    color: red;
    font-size: 13px;
}
</style>