<script lang="ts">
import CompContent from "./components/Content/CompContent.vue";
import CompHeader from "./components/Content/CompHeader.vue";
export default {
    name: "App",
    components: {
        CompContent,
        CompHeader
    },
};
</script>
<template>
    <div class="container m-5 p-2 rounded mx-auto bg-light shadow">
        <div class="main">
            <CompHeader />
            <CompContent></CompContent>
        </div>
    </div>
</template>
<style scoped>
body {
    font-family: "Open Sans", sans-serif;
    line-height: 1.6;
}

CompContent {
    margin-bottom: 30px;
    ;
}

.add-todo-input,
.edit-todo-input {
    outline: none;
}

.add-todo-input:focus,
.edit-todo-input:focus {
    border: none !important;
    box-shadow: none !important;
}

.view-opt-label,
.date-label {
    font-size: 0.8rem;
}

.edit-todo-input {
    font-size: 1.7rem !important;
}

.todo-actions {
    visibility: hidden !important;
}

.todo-item:hover .todo-actions {
    visibility: visible !important;
}

.todo-item.editing .todo-actions .edit-icon {
    display: none !important;
}
</style>
