<template>
    <input 
    type="radio"
    :id="id"
    :name="name">
    <label :for="id">{{ label }}</label>
</template>
<script>
export default {
    props: {
        label: { required: true, type: String },
        done: { default: false, type: Boolean },
        id: { required: true, type: String },
        name: {required: true, type: String }
    },
}
</script>
<style scoped>

</style>