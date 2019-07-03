<template>
    <div id="app">
        <b-navbar toggleable="lg" type="dark" variant="dark">
            <b-navbar-brand href=" ">JSONPlaceholder</b-navbar-brand>
            <b-collapse id="nav-collapse" is-nav>
                <b-navbar-nav class="ml-auto">
                    <b-navbar-nav right>
                        <b-nav-item to="posts">POSTS</b-nav-item>
                        <b-nav-item to="comments">COMMENTS</b-nav-item>
                        <b-nav-item to="albums">ALBUMS</b-nav-item>
                        <b-nav-item to="photos">PHOTOS</b-nav-item>
                        <b-nav-item to="todos">TODOS</b-nav-item>
                        <b-nav-item to="users">USERS</b-nav-item>
                    </b-navbar-nav>
                </b-navbar-nav>
            </b-collapse>
        </b-navbar>

            <router-view />

    </div>
</template>

<script>
require('@/assets/styles/App.css')
require('@/assets/styles/table.css')
export default {
    name: 'App'
}
</script>
