<template>
    <div>
        <div class="card mb-4" v-for="blog in blogs">
            <div class="card-header"><a href="#" style="color: brown">{{ blog.title}} </a></div>
            <div class="card-body">
                {{ blog.body }}
                <br/>
                <p>Written By {{blog.user.name}}</p>
            </div>
        </div>
    </div>
</template>

<script>
    import axios from 'axios';

    export default {
        data() {
            return {
                blogs: []
            }
        },
        methods: {
            getBlogs: function () {
                axios.get('/api/guest/blogs')
                    .then(({data}) => {
                        console.log(data.data);
                        this.blogs = data.data;
                    }, () => {

                    });
            }
        },
        mounted() {
            this.getBlogs();
        }

    }
</script>
