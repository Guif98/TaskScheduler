<template>
<div :class="[task.reminder ? 'reminder' : '', 'task']">
    <h3>{{ task.text }}
        <i @click="onDelete(task.id)" class="fas fa-times float-right"></i>
    </h3>
    <p>{{ task.day }}</p>
</div>
</template>

<script>

export default ({
    name: 'Task',
    props: {
        task: Object
    },
    methods: {
        onDelete(id) {
            this.$emit('delete-task', id)
        }
    }
})
</script>

<style>

.fas {
    text-align: end;
    color: red;
}

.float-left {
    float: right;
}

    .task {
        background: rgb(95, 70, 70);
        margin: 5px;
        padding: 10px 20px;
        cursor: pointer;
        color: white;
    }

    .task.reminder {
        border-left: 10px solid rgb(31, 122, 58);
    }

    .task h3 {
        display: flex;
        align-items: center;
        justify-content: space-between;
        font-weight: bold;
    }

</style>