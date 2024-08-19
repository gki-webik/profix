<script>
export default {
    mounted() {
        let MWKStyle = document.createElement('link');
        MWKStyle.setAttribute('href', 'https://gki-wbk.ru/files/lib/mwk/mwk.min.css');
        MWKStyle.setAttribute('rel', 'stylesheet');
        document.head.appendChild(MWKStyle);
        let MWKScript = document.createElement('script');
        MWKScript.setAttribute('src', 'https://gki-wbk.ru/files/lib/mwk/mwk.min.js');
        document.body.appendChild(MWKScript);
    },
    data() {
        return {
            city: "Omsk",

        }
    },
    methods: {
        fetchAPI(url) {
            fetch(url, {
                method: 'POST',
                headers: {
                    'Content-Type': 'application/json'
                },
                body: JSON.stringify({
                    'type': 'link', 'method': 'add', "content": "https://example.com"
                })
            })
                .then(res => res.json())
                .then((data) => { console.log(data) })
                .catch((err) => { console.log(err) });
        }
    }
}
</script>
<template>
    <div className="main">
        <input type="text" className="wk-input" v-model="city">
        <button className="wk-btn is-fullwidth is-primary" @click="fetchAPI('https://gki-wbk.ru/api/klicks/api.php')"
            v-show="this.city !== ''">Клац</button>
        {{ city }}
    </div>
</template>

<style scoped>
.main {
    height: 100vh;
    display: flex;
    flex-direction: column;
    color: #ddd;
    gap: 10px;
    align-items: center;
    justify-content: center;
    max-width: 300px;
    margin: 0 auto;
}

h1 {
    color: #ddd;
}
</style>
