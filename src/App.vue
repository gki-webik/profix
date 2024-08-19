<script>
let id = 0
export default {
    data() {
        return {
            myName: "",
            array: [],
        }
    },
    methods: {
        pushScopeId() {

            this.myName == "" || this.array.push(
                {
                    id: id++,
                    name: this.myName
                }
            );
            this.myName = "";
        }
    }
}
</script>

<template>
    <div class="main">
        <input type="text" v-model="myName">
        <button @click="pushScopeId()">Отправить</button>
        <div v-for="e in array" :key="e.id">
            {{ e.name }}
        </div>
        <div v-if="array.length == 0">
            Элементов нет
        </div>
        <div v-else>
            Сейчас {{ array.length }} элемента
        </div>
    </div>
</template>

<style scoped>
.main {
    height: 100vh;
    display: flex;
    flex-direction: column;
    color: #ddd;
    align-items: center;
    justify-content: center;
}

h1 {
    color: #ddd;
}
</style>
