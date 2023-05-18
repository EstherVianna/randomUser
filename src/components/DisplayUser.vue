<script setup>
defineProps({
    userState: Object,
    colorName: String,
    userName: String,
    colorCode: String,
    showDescription: Function,
    avatar: String,
});

</script>
<template>
<h1 class="meetings">Here is {{ userState.first_name }}, click for next profile!</h1>
<div class="card">
  <div class="card-side">
        <p class="card-side-title">{{ userName }}</p>
        <p class="card-side-favColor">Fav color: {{ colorName }}</p>
        <span class="card-side-color-circle" :style="{'background-color': colorCode}">
        </span> 
        <p>{{ showDescription }}</p>
    </div>
        <div class="card-image">
            <img :src="avatar" alt="image1">
        </div>
</div>
    
</template>

<style scoped lang="sass">
.meetings
    text-align: center
    color: #000
    margin-bottom: 36px
.card 
    width: 90%
    height: 70%
    background: linear-gradient(106.37deg, #DC29AB -71.14%, #FF865C -14.61%, #FF4A80 44.57%, #743ECD 98.45%)
    box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25)
    border-radius: 10px
    padding: 20px
    display: flex
    gap: 15px
    justify-content: space-between
    align-self: center
    margin: auto
    &-image 
        width: 100px
        height: 100px
        background: rgba(0, 0, 0, 0.26)
        display: flex
        align-items: center
        justify-content: center
        img
            border-radius: 5px
    &-side 
        width: 300px
        &-title
            font-weight: 700
            font-size: 20px
            line-height: 15px
            display: flex
            align-items: center
        &-favColor 
            margin: 10px 0 0 0
            font-weight: bold
            font-size: 13px
            line-height: 15px
        &-color-circle 
            display: inline-flex
            width: 40px
            height: 40px
            border: 2px solid #d8d8d8
            border-radius: 50%
</style>