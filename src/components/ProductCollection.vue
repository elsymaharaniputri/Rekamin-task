<template>
    <div class="collection-container my-5">
        <!-- Judul Kategori -->
        <div class="d-flex justify-content-between align-items-start mb-3">
            <h5 class="fw-bold text-uppercase">{{ title }}</h5>
        </div>

        <!-- Wrapper isi -->
        <div class="d-flex align-items-center justify-content-between flex-wrap rounded-4 p-4"
            style="background-color: #E8E8E8;">
            <!-- Gambar kiri -->
            <div class="image-wrapper" style="flex: 1; text-align: center;">
                <img :src="sideImage" alt="Model" class="rounded-4"
                    style="width: 250px; height: auto; object-fit: cover;" />
            </div>

            <!-- Produk utama -->
            <div class="product-detail d-flex flex-column justify-content-center px-4" style="flex: 2;">
                <div class="d-flex flex-column">
                    <p class="text-muted mb-1 small">{{ currentProduct.category }}</p>
                    <h6 class="fw-bold">{{ currentProduct.title }}</h6>
                    <p class="small text-muted mb-1">— Only {{ currentProduct.rating?.count }} pcs</p>

                    <p class="small mt-2" style="text-align: justify;">
                        {{ currentProduct.description }}
                    </p>

                    <div class="d-flex align-items-center gap-3 mt-2">
                        <p class="fw-semibold mb-0">$ {{ currentProduct.price }}</p>
                        <p class="fw-semibold mb-0">
                            ⭐ {{ currentProduct.rating?.rate }}/5
                        </p>
                    </div>

                    <button class="btn btn-outline-dark btn-sm rounded-pill px-4 mt-3">
                        Checkout
                    </button>
                </div>
            </div>

            <!-- Tombol Navigasi -->
            <div class="d-flex flex-column justify-content-center align-items-center gap-2">
                <button @click="prevProduct" class="btn btn-outline-dark btn-sm rounded-circle">
                    <i class="bi bi-arrow-left"></i>
                </button>
                <button @click="nextProduct" class="btn btn-outline-dark btn-sm rounded-circle">
                    <i class="bi bi-arrow-right"></i>
                </button>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: "ProductCollection",
    props: {
        title: String,
        products: Array,
        sideImage: String,
    },
    data() {
        return {
            currentIndex: 0,
        };
    },
    computed: {
        currentProduct() {
            return this.products[this.currentIndex] || {};
        },
    },
    methods: {
        nextProduct() {
            if (this.currentIndex < this.products.length - 1) this.currentIndex++;
            else this.currentIndex = 0;
        },
        prevProduct() {
            if (this.currentIndex > 0) this.currentIndex--;
            else this.currentIndex = this.products.length - 1;
        },
    },
};
</script>

<style scoped>
.collection-container img {
    border-radius: 20px;
}

.btn-outline-dark {
    transition: all 0.2s ease;
}

.btn-outline-dark:hover {
    background-color: black;
    color: white;
}
</style>
