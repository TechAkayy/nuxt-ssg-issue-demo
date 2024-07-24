<script setup>
const route = useRoute()


const slug = route.params.slug

const endpoint = 'https://jsonplaceholder.typicode.com/posts/' + slug

const { data: article } = await useFetch(endpoint, {
    key: 'articles-' + route.params.slug,
    // Call this endpoint only on the server
    server: true
})

// Hint nitro to prerender a json file for this endpoint
prerenderRoutes(endpoint)
</script>


<template>
    <div>
        <div class="">
            <h2 class="text-4xl font-bold text-cyan-600">{{ article.title }}</h2>
            <div class="my-5">
                <div>{{article.body}}</div>
            </div>
        </div>
    </div>
</template>
