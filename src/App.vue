<script>
import MyLinks from "./components/MyLinks.vue"
export default {
    components: { MyLinks },
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
                    /* body: JSON.stringify({
                        'key': 'WK255', 'type': 'link', 'method': 'add', "content": this.link
                    }) */
                    body: JSON.stringify({
                        "username": "root",
                        "password": "555"
                    }),
                    headers: {
                        'Authorization': "Bearer " + localStorage.getItem('token')
                    }
                })
                    .then(res => res.json())
                    .then((data) => {
                        this.info = data;
                    })
                    .catch((err) => { console.log(err); });
                return;
            }
            fetch(url)
                .then(res => res.json())
                .then((data) => { this.info = data })
                .catch((err) => { console.log(err); });
        },
        clearLink() {
            this.info = ""
        }
    }
}
</script>
<template>
    <div className="main">
        <input type="text" className="wk-input" v-model="link">
        <button className="wk-btn is-fullwidth is-primary"
            @click="fetchAPI('https://magic-wk.ru/protected.php', 'POST')" v-show="this.link !== ''">Клац</button>
        <br>
        <MyLinks :myLink="this.info" :clearLink="clearLink" />
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
