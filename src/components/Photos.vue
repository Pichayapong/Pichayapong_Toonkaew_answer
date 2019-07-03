<template>
    <div id="photos">
        <b-container>
            <b-navbar>
                <b-navbar-brand>Photos</b-navbar-brand>
                <b-collapse id="nav-collapse" is-nav>
                    <b-navbar-nav class="ml-auto">
                        <b-navbar-nav right>
                            <b-row>
                                <b-nav-form>
                                    <b-form-input
                                        size="sm"
                                        class="mr-sm-2"
                                        v-model="dalbumId"
                                        placeholder="Enter album id"
                                    ></b-form-input>
                                    <b-button
                                        size="sm"
                                        type="submit"
                                        class="my-2 my-sm-0"
                                        @click="searchData(dalbumId)"
                                    >search</b-button>
                                </b-nav-form>
                            </b-row>
                        </b-navbar-nav>
                    </b-navbar-nav>
                </b-collapse>
            </b-navbar>

            <b-row v-if="loading" class="text-center" style="justify-content: center">
                <b-spinner variant="success" label="Spinning"></b-spinner>
            </b-row>
            <b-row v-else>
                <table class="table">
                    <tr>
                        <th>Album Id</th>
                        <th>Id</th>
                        <th>Title</th>
                        <th>URL</th>
                        <th>Thumbnail</th>
                        <th>Delete</th>
                    </tr>
                    <tr v-for="(post, key) in posts" :key="post.id">
                        <td>{{post.albumId}}</td>
                        <td>{{post.id}}</td>
                        <td>{{post.title}}</td>
                        <td>
                            <a v-bind:href="post.url" target="_blank">{{post.url}}</a>
                        </td>
                        <td>
                            <img :src="post.thumbnailUrl" />
                        </td>
                        <td>
                            <b-button-group vertical>
                                <!-- <b-button variant="success">EDIT</b-button> -->
                                <b-button @click="deleteData(post.id,key)" variant="danger">X</b-button>
                            </b-button-group>
                        </td>
                    </tr>
                </table>
            </b-row>
        </b-container>
    </div>
</template>

<script>
import axios from 'axios'
export default {
    name: 'Photos',
    data() {
        return {
            loading: false,
            errors: [],
            posts: [],
            dalbumId: ''
            // did: '',
            // dtitle: '',
            // dbody: ''
        }
    },
    created: function() {
        this.loading = true
        axios
            .get('https://jsonplaceholder.typicode.com/photos')
            .then(respond => {
                this.loading = false
                this.posts = respond.data
            })
            .catch(e => {
                this.loading = false
                this.errors.push(e)
            })
    },
    methods: {
        deleteData(id, i) {
            axios
                .delete('https://jsonplaceholder.typicode.com/photos/' + id, {
                    method: 'DELETE'
                })
                .then(res => {
                    this.posts.splice(i, 1)
                })
                .catch(e => {
                    this.loading = false
                    this.errors.push(e)
                })
        },
        searchData(id) {
            var myid = ''
            if (id) {
                myid = '?albumId=' + id
            }
            axios
                .get('https://jsonplaceholder.typicode.com/photos' + myid)
                .then(res => {
                    this.loading = false
                    this.posts = res.data
                })
                .catch(e => {
                    this.loading = false
                    this.errors.push(e)
                })
        }
    }
}
</script>




