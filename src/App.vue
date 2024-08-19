<script>
import User from "./components/User.vue"

let id = 0
export default {
    components: { User },
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
        },
        delUser(index) {
            this.array.splice(index, 1);
        }
    }
}
</script>

<template>
    <div class="main">
        <input type="text" v-model="myName">
        <button @click="pushScopeId()">Отправить</button>
        <User v-for="(user, index) in array" :key="index" :user="user" :indexUser="index" :delUser="delUser" />
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
