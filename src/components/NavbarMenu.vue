<template>
    <nav class="navbar navbar-expand-lg bg-light shadow-sm px-4 py-3">
        <div class="container-fluid">
            <a class="navbar-brand fw-bold" href="#">FashionKU</a>
            <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav">
                <span class="navbar-toggler-icon"></span>
            </button>

            <div class="collapse navbar-collapse" id="navbarNav">
                <ul class="navbar-nav mx-auto mb-2 mb-lg-0">
                    <li class="nav-item"><a class="nav-link active text-warning fw-semibold" href="#">Home</a></li>
                    <li class="nav-item"><a class="nav-link" href="#">Man Clouthing</a></li>
                    <li class="nav-item"><a class="nav-link" href="#">Woman Clouthing</a></li>
                    <li class="nav-item"><a class="nav-link" href="#">New Collection</a></li>
                </ul>

                <div class="d-flex">
                    <button class="btn btn-outline-dark me-2">Sign Up</button>
                    <button class="btn btn-dark">Login</button>
                </div>
            </div>
        </div>
    </nav>
</template>

<script>
export default {
    name: 'NavbarMenu'
}
</script>
