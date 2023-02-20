<template>
    <nav class="navbar navbar-expand-lg bg-body-tertiary">
        <div class="container-fluid m-4">

            <div class="ms_logo-container">
                <a href="#">
                    <img src="../assets/cooder-logo.png" alt="cooder-logo">
                </a>
            </div>

            <div class="collapse navbar-collapse" id="navbarSupportedContent">

                <ul class="navbar-nav me-auto mb-2 mb-lg-0">
                    <li class="nav-item ms_nav-buttom ms_bg-green">
                        <a class="nav-link active" aria-current="page" href="#">Home</a>
                    </li>
                </ul>

                <form class="d-flex" role="search">
                    <input class="form-control me-2 ms_search-bar" type="search" placeholder="search..."
                        aria-label="Search">
                    <button class="btn btn-light ms_nav-btn" type="submit" @click.prevent="">
                        <i class="fa-solid fa-magnifying-glass "></i>
                    </button>
                </form>

            </div>

        </div>
    </nav>
</template>

<script>
export default {

}
</script>

<style lang="scss">
@import "../styles/mixins.scss";
@import "../styles/general.scss";

div.ms_logo-container{
    width: 100px;
    margin-right: 20px;
    
    img{
        width: 100%;
    }
}

li.ms_nav-buttom{
    @include button-style;
    margin-top: 6px;

    a{
        padding: 0;
    }
    
}

input.ms_search-bar{
    border-radius: 20px;
}

button.ms_nav-btn{
    background-color: black;
    color: white;
    border-radius: 20px;
}

</style>