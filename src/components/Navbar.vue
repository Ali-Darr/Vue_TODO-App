<script setup>
import { RouterLink } from 'vue-router';
</script>

<template>
    <nav class="navbar navbar-expand-lg bg-light">
        <div class="container-fluid">
            <RouterLink class="navbar-brand" to="/">Vue Todos</RouterLink>
            <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent"
                aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
                <span class="navbar-toggler-icon"></span>
            </button>
            <div class="collapse navbar-collapse" id="navbarSupportedContent">
                <ul class="navbar-nav me-auto mb-2 mb-lg-0">
                    <li class="nav-item">
                        <RouterLink class="nav-link" :class="{ active: $route.name === 'home' }" aria-current="page" to="/">
                            Home</RouterLink>
                    </li>
                    <li class="nav-item">
                        <RouterLink class="nav-link" :class="{ active: $route.name === 'about us' }" aria-current="page"
                            to="/about-us">About Us</RouterLink>
                    </li>
                    <li class="nav-item">
                        <RouterLink class="nav-link" :class="{ active: $route.name === 'contact us' }" aria-current="page"
                            to="/contact-us">Contact Us</RouterLink>
                    </li>
                </ul>
                <form class="d-flex" role="search">
                    <button class="btn btn-primary" type="button">Toggle</button>
                </form>
            </div>
        </div>
    </nav>
</template>

<style lang="scss" scoped>
.active {
    font-weight: bold;
}
</style>