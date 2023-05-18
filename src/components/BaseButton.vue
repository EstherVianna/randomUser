<script setup>

defineEmits(['randomize']);

</script>

<template>
<button @click="$emit('randomize')" class="change-user-btn">Random User</button>

</template>

<style scoped lang="sass">
.change-user-btn
    display: flex
    justify-content: center
    align-items: center
    margin: auto
    padding: 10px 20px
    margin-top: 36px
    transition: all ease 0.1s
    box-shadow: 0px 5px 0px 0px #a29bfe
    &:active
        transform: translateY(5px)
        box-shadow: 0px 0px 0px 0px #a29bfe


</style>