<template>
    <div>
        <h2>{{ articleDetail?.title }}</h2>
        <p>{{ articleDetail?.description }}</p>
    </div>
</template>

<script lang="ts">
import { defineComponent, ref, onMounted } from 'vue'
import axios from 'axios'

export default defineComponent({
    name: 'ArticleDetail',
    props: {
        articleId: {
            type: Number,
            required: true
        }
    },
    data() {
        return {
            articleDetail: null
        }
    },

    methods: {
        getArticle(articleId: number) {
            const articleUrl = `https://6082e3545dbd2c001757abf5.mockapi.io/qtim-test-work/posts/${articleId}`
            axios
                .get(articleUrl)
                .then((response) => {
                    this.articleDetail = response.data
                    console.log('articleDetail:', this.articleDetail)
                })
                .catch((error) => {
                    console.log('Error fetching article data:', error)
                })
        },

    },
    async mounted() {
        this.getArticle(this.articleId)
    },

})
</script>

<style scoped lang="less">
</style>