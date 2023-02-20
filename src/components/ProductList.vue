<template>
    <section>

        <div class="ms_filter-box">
            <h1>CHOOSE YOUR CATEGORY</h1>
            <div>
                <select name="" id="select-category" v-model="selectedCategory"
                    @change="filteredCategories(selectedCategory)">
                    <option selected value="">All categories</option>
                    <option v-for="category in categories" :key="category.id" :value="category">{{ category }}</option>
                </select>
            </div>
        </div>

        <div class="mb-5">
            <span>Sort:</span>
            <i class="fa-solid fa-arrow-up-wide-short mx-1"></i>
            <i class="fa-solid fa-arrow-down-wide-short"></i>
        </div>

        <div class="row g-5">
            <ProductCard v-for="productDetail in filteredProductDetails" :key="productDetail.id"
                :productDetail="productDetail" />
        </div>

    </section>

</template>

<script>
import axios from 'axios';
import ProductCard from './ProductCard.vue'

export default {
    name: 'ProductList',

    data: function () {
        return {
            productDetails: [],
            filteredProductDetails: [],
            categories: [],
            selectedCategory: '',
            apiURL: 'https://fakestoreapi.com/products',
        }
    },

    components: {
        ProductCard,
    },

    methods: {

        getProductDetailsAll() {
            axios.get(this.apiURL)
                .then((result) => {
                    console.log(result.data)
                    this.productDetails = result.data;
                    this.filteredProductDetails = result.data;
                    this.categories = this.getUniqueCategory(this.productDetails);
                    console.log(this.categories);

                })
                .catch((error) => {
                    console.warn(error);
                })
        },

        getUniqueCategory(productDetails) {
            const category = [];
            productDetails.forEach(productDetail => {
                if (!category.includes(productDetail.category)) {
                    category.push(productDetail.category);
                }
            });
            return category;
        },

        filteredCategories(category) {
            if(category == null || category === ''){
                this.filteredProductDetails = this.productDetails;
            } else {
                this.filteredProductDetails = this.productDetails.filter(element => element.category === category);
            }
        },
    },

    created() {
        this.getProductDetailsAll();
    },

}
</script>

<style lang="scss" scoped>
.ms_sort-tool a {
    color: black;
}

select {
    border: 3px dashed black;
    border-radius: 20px;
    padding: 4px 10px;
    background-color: #D2FE56;
    color: rgb(114, 113, 113)
}
</style>