<template>
    <div>
        <h1 class="main-headline">{{ articleDetail?.title }}</h1>
        <img class="main-img" :src="articleDetail?.image" alt="picture">
        <p class="article-text">{{ articleDetail?.description }}</p>
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
.main-headline {
    color: #101010;
    font-size: 84px;
    font-weight: 400;
    line-height: 84px;
}

.article-text {
    font-size: 36px;
    font-weight: 400;
    line-height: 44px;
    color: #101010;
}

.main-img {
    display: block;
    width: 1216px;
    // height: 700px;
    max-width: 100%;
    aspect-ratio: 16/9;
    background-color: rgb(243, 243, 243);
}
</style>