<script setup>

const props = defineProps({
    todo: {
        type: Object,
        required: true,
        // default() {
        //     return {}
        // }
    },
    index: {
        type: Number,
        required: true,
    },
})

defineEmits(["toggle-complete"])

</script>

<template>
    <tr :class="{ 'complete-tudo': todo.isCompleted }">
        <th scope="row">
            <input class="form-check-input p-2" type="checkbox" :checked="todo.isCompleted"
                @input="$emit('toggle-complete', index)">
        </th>
        <td>{{ todo.tname }}</td>
        <td>{{ todo.tmail }}</td>
        <td>{{ todo.ttime }}</td>
    </tr>
</template>

<style scoped>
input[type="checkbox"] {
    &:checked {
        background-color: green;
    }
}

.complete-tudo {
    text-decoration: line-through;
}
</style>