<template>
    <div class="submission">
        <div class="form-container">
            <input type="text" class="message" v-model="message">
            <button class="submit" @click="submit">↑</button>
        </div>
    </div>
</template>

<script>
export default {
    name: "InputForm",
    data: () => {
        return {
            message: ''
        }
    },
    methods: {
        submit () {
            this.$emit('submitted', this.message)
            this.message = ''
        }
    }
}
</script>

<style scoped>
    .submission {
        text-align: center;
    }
</style>
