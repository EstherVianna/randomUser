<script setup>
import { reactive, computed, onMounted } from 'vue';
import DisplayUser from '../components/DisplayUser.vue';
import BaseButton from '../components/BaseButton.vue';

const state = reactive({
    users: [],
    userId: 1,
    colorName: "",
    colorCode: ""
});

const descriptions = [
        "36 anos, George é um aventureiro e já escalou o Monte Everest, a montanha mais alta do mundo.",
        "45 anos, Janet é uma adepta de ioga há mais de uma década e consegue realizar posições avançadas facilidade.",
        "32 anos, Emma é uma entusiasta de jardinagem e já cultivou mais de 50 tipos diferentes de flores em seu jardim.",
        "50 anos, Eve é um amante da gastronomia e já experimentou pratos exóticos de mais de 10 países diferentes.",
        "28 anos, Charles é um ávido leitor e já leu mais de 500 livros de diversos gêneros literários.",
        "41 anos, Tracey é um talentoso artista plástico e já realizou exposições de suas obras em várias galerias renomadas."
];

const getUsers = async () => {
    const url = await fetch(`https://reqres.in/api/users/${state.userId}`);
    const json = await url.json();
    state.users = json.data;
};

const getFavColor = async () => {
  const url = await fetch(`https://reqres.in/api/unknown`);
  const json = await url.json();
  const data = json.data;
  const colorObject = data.find(obj => obj.id === state.userId);
  state.colorName = colorObject.name;
  state.colorCode = colorObject.color;
};

const id = () => {
    return Math.floor(Math.random() * 6) + 1;
};

state.userId = id();

const newId = (currentId) => {
    let randomId;
    do {
        randomId = id();
    } while (randomId === currentId);
  return randomId;
};

const newUser = ()=> {
    state.userId = newId(state.userId);
    getUsers();
    getFavColor();
};

const showDescription = ()=> {
    switch (state.userId) {
        case 1:
            return descriptions[0]
            
        case 2:
            return descriptions[1]
            
        case 3:
            return descriptions[2]
            
        case 4:
            return descriptions[3]

        case 5:
            return descriptions[4]
        
        case 6:
            return descriptions[5]
    }
};

onMounted(async ()=> {
    await getUsers()
    await getFavColor()
});

const color = computed(()=> state.colorName);
const fullName = computed(() => `${state.users.first_name} ${state.users.last_name}`);
const avatar = computed(()=> state.users.avatar);
const colorHex = computed(()=> state.colorCode);

</script>
<template>
    <div class="container">
        <DisplayUser :user-state="state.users" :user-name="fullName" :color-name="color" :color-code="colorHex" :show-description="showDescription()" :avatar="avatar" :user-id="state.userId">
        </DisplayUser>
        <div>
            <BaseButton @randomize="newUser()"/>
        </div>
    </div>
</template>
<style scoped lang="sass">
</style>
