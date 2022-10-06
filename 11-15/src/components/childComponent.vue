<script>
    export default {
        emits: ["response"],
        created() {
            this.$emit("response", "-m \"initial comit\"")
        },
        props: {
            msg: String,
        }
    }
</script>

<template>
    <h1>Alo</h1>
    <slot>vas ne slyshno</slot>
</template>