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
            info: "",
            link: "",
            error: ""
        }
    },
    methods: {
        fetchAPI(url, method) {
            if (method === "POST") {
                fetch(url, {
                    method: 'POST',
                    body: JSON.stringify({
                        'key': 'WK255', 'type': 'link', 'method': 'add', "content": this.link
                    })
                })
                    .then(res => res.json())
                    .then((data) => { this.info = data })
                    .catch((err) => { console.log(err); });
                return;
            }
            fetch(url)
                .then(res => res.json())
                .then((data) => { this.info = data })
                .catch((err) => { console.log(err); });
        }
    }
}
</script>
<template>
    <div className="main">
        <input type="text" className="wk-input" v-model="link">
        <button className="wk-btn is-fullwidth is-primary" @click="fetchAPI('https://gki-wbk.ru/api/klicks/v2', 'POST')"
            v-show="this.link !== ''">Клац</button>
        <br>
        {{ info }}
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
