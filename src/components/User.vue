<template>
    <div>
        {{ user.name }}
        {{ indexUser }}
        <button type="button" @click="delUser(indexUser)">Удалить</button>
    </div>
</template>

<script>

export default {
    props: {
        user: {
            type: Object,
            required: true
        },
        indexUser: {
            type: Number,
            required: true
        },
        delUser: {
            type: Function,
            required: true
        }
    }
}

</script>