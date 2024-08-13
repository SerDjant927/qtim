<template>
    <section class="articles container container_inner">
        <div v-if="selectedArticleId">
            <ArticleDetail :articleId="selectedArticleId" />
            <button @click="resetSelectedArticle">Вернуться к списку статей</button>
        </div>
        <div v-else>
            <ul class="article-list">
                <li v-for="article in paginatedArticles" :key="article.id" @click="getArticle(article.id)"
                    class="article-list__item">
                    <a class="article" href="javascript:void(0)">
                        <picture style="width: 280px; height: 280px; background-color: #F3F3F3;">
                            <source :srcset="article.image" />
                            <img height="280" width="280" class="article__img" :src="article.image" alt="Img" />
                        </picture>
                        <span class="article__descr">{{ article.title }}</span>
                        <span class="article__clickbait">Read more</span>
                    </a>
                </li>
            </ul>
            <ul class="pagination">
                <li @click="setCurrentPage(pageNumber)" class="pagination__item" :class="{ pagination__item_active: pageNumber === currentPage }"
                    v-for="pageNumber in Math.min(pageCount, 5)" :key="pageNumber">
                    {{ pageNumber }}
                </li>
                <li @click="goToNextPage" class="pagination__item pagination__item_more" v-if="pageCount > 5">
                    <svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                        <path d="M9.5 7.5L14.5 12.5L9.5 17.5" stroke="#494949" stroke-width="1.3" stroke-linecap="round"
                            stroke-linejoin="round" />
                    </svg>
                </li>
            </ul>
        </div>

    </section>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue'
import axios from 'axios'
import ArticleDetail from './ArticleDetail.vue'

export default defineComponent({
    name: 'ArticlesList',
    components: {
        ArticleDetail
    },
    data() {
        return {
            articleList: [],
            currentPage: 1,
            articlesPerPage: 8,
            articleDetail: null,
            selectedArticleId: null
        }
    },
    computed: {
        paginatedArticles() {
            const startIndex = (this.currentPage - 1) * this.articlesPerPage
            const endIndex = startIndex + this.articlesPerPage
            return this.articleList.slice(startIndex, endIndex)
        },
        pageCount() {
            return Math.ceil(this.articleList.length / this.articlesPerPage)
        }
    },
    methods: {
        getArticles() {
            const ArticlesList = 'https://6082e3545dbd2c001757abf5.mockapi.io/qtim-test-work/posts/'
            axios
                .get(ArticlesList)
                .then((response) => {
                    this.articleList = response.data
                    console.log(this.articleList)
                })
                .catch((error) => {
                    console.log('Error fetching articles:', error)
                })
        },
        setCurrentPage(pageNumber: number) {
            this.currentPage = pageNumber
        },
        goToNextPage() {
            if (this.currentPage < this.pageCount) {
                this.setCurrentPage(this.currentPage + 1)
            }
        },
        getArticle(articleId: number) {
            const articleUrl = `https://6082e3545dbd2c001757abf5.mockapi.io/qtim-test-work/posts/${articleId}`
            axios
                .get(articleUrl)
                .then((response) => {
                    this.articleDetail = response.data
                    console.log(this.articleDetail)
                    this.selectedArticleId = articleId
                })
                .catch((error) => {
                    console.log('Error fetching article data:', error)
                })
        },
        resetSelectedArticle() {
            this.selectedArticleId = null;
        }
    },
    created() {
        this.getArticles()
    }
})
</script>
<style scoped lang="less">
.article {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    justify-content: flex-start;
    text-decoration: none;

    &__descr {
        color: #101010;
        font-size: 20px;
        font-weight: 400;
        line-height: 24px;
        margin-top: 24px;
    }

    &__clickbait {
        color: #e2beff;
        font-size: 20px;
        font-weight: 400;
        line-height: 24px;
        height: 0px;
        transition: all 0.3s;
        opacity: 0;
        margin-top: 0;
    }

    &:hover {
        .article__clickbait {
            opacity: 1;
            height: 24px;
            margin-top: 12px;
        }
    }

    img {
        background-color: #F3F3F3;
    }
}

.article-list {
    display: flex;
    flex-wrap: wrap;
    column-gap: 32px;
    row-gap: 40px;
    margin: 0;
    padding: 0;
    list-style: none;

    &__item {
        display: flex;
        flex-direction: column;
        width: 280px;
        padding-top: 36px;

        &:hover {
            padding-top: 0;
        }
    }
}

.pagination {
    margin: 0;
    padding: 0;
    list-style: none;
    display: flex;
    column-gap: 8px;

    &__item {
        color: #101010;
        font-size: 16px;
        font-weight: 400;
        line-height: 8px;
        background-color: #F3F3F3;
        border-radius: 10px;
        height: 44px;
        width: 44px;
        margin-top: 50px;
        display: flex;
        align-items: center;
        justify-content: center;
        cursor: pointer;

        &_active {
            background-color: #101010;
            color: #fff;
        }
    }
}
</style>