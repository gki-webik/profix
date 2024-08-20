<template>
    {{ myLink }} <button className="wk-btn" v-show="myLink != ''" @click="clearLink">Очистить</button>
</template>

<script scoped>
export default {
    props: {
        myLink: Object,
        clearLink: Function
    }
}
</script>