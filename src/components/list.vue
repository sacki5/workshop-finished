<template>
    <ul id="list">
        <li
            v-for="(item, index) in items"
            :key="index"
            @click="$emit('clickedItem', index)"
        >
            {{ item }}
        </li>
    </ul>
</template>

<script>
export default {
    props: {
        items: { type: Array, required: true },
    },
};
</script>
