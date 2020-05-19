<template>
    <div class="conversation-balloon" :class="speaker">
        <p class="message">{{ name }}: {{ message }}</p>
    </div>
</template>

<script>
export default {
    name: "Item",
    props: {
        name: {
            type: String,
            required: true
        },
        speaker: {
            type: String,
            required: true
        },
        message: {
            type: String,
            required: true
        }
    },
}
</script>

<style scoped lang="scss">
    $balloon-color: #FFF;

    .conversation-balloon {
        &.me {
            background-color: $balloon-color;
            text-align: right;
        }
        &.other {
            background-color: $balloon-color;
            text-align: left;
        }
    }
</style>
