<template>
    <main class="container my-5">
        <ProductList/>
    </main>
</template>

<script>

import ProductList from './ProductList.vue'

export default {
    name: 'SiteMain',
    components: {
        ProductList,

    },

}
</script>

<style lang="scss">
@import "../styles/mixins.scss";
@import "../styles/general.scss";


div.ms_filter-box{
    text-align: center;
    margin-bottom: 120px;
    
    h1{
        font-size: 6rem;
    }

    div ul{
        list-style: none;
        
        li{
            display: inline;
            margin: 0 6px;
            @include button-style;
            
            &:hover{
                cursor: pointer;
                border: solid;
            }
        }
    }
}
</style>