<template>
    <div class="home">
        <img src="@/assets/BG.png" />
        <div id="sometext">
            <h1>Vue.js project with JSONPlaceholder</h1>
            <p>Fake Online REST API for Testing and Prototyping</p>
        </div>
        <footer>
            <div>
                <h3>Directed by Pichayapong Toonkaew</h3>
                <p><b>Call:</b> 061-287-6360</p>
                <p><b>Email:</b> pichayapong.t@gmail.com</p>
                <p><b>Facebook:</b> Pichayapong Toonkaew</p>
            </div>
        </footer>
    </div>
</template>

<script>
export default {
    name: 'Home'
}
</script>

<style>
.home {
    text-align: center;
}
#sometext {
    text-align: center;
    padding-bottom: 2em;
}
footer {
    border-top: 2px solid rgb(129, 129, 129);
    padding-top: 2em;
    color: black;
    width: 100%;
}
</style>
