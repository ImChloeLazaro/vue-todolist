<script>
export default {
    data() {
        return {
            name: '',
        }
    },
    methods: {
        register() {
            this.$emit('register', this.name)
            this.name = ''
        },
    }
}
</script>
<template>
    <form @submit.prevent="register">
        <input class="form-control form-control-sm" type="text" placeholder="Enter your name" v-model="name"
            aria-label=".form-control-sm example">
        <button type="submit" class="btn btn-primary">Save changes</button>
    </form>
</template>