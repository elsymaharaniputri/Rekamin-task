<template>
    <div class="container py-5">
        <h5 class="fw-bold mb-4">New Collection</h5>

        <!-- Wrapper utama -->
        <div class="d-flex gap-4 align-items-start flex-wrap">

            <!-- Bagian katalog produk -->
            <div class="d-flex flex-wrap gap-3">
                <div v-for="(item, index) in selectTop()" :key="index" class="rounded-4 overflow-hidden"
                    style="width: 230px;  cursor: pointer; transition: transform 0.3s;"
                    @mouseover="selectedProduct = item" @mouseleave="selectedProduct = null">
                    <!-- Bagian gambar berwarna -->
                    <div class="p-3 d-flex align-items-center justify-content-center" :style="{
                        backgroundColor: bgColors[index % bgColors.length],
                        height: '300px',
                    }">
                        <img :src="item.image" alt="product" style="height: 100px; object-fit: contain;" />
                    </div>

                    <!-- Bagian card putih di bawah -->
                    <div class="bg-white text-center py-2 rounded-bottom-4 shadow-sm">
                        <p class="text-muted mb-0 small"> {{ item.category }}</p>
                        <p class="fw-semibold text-capitalize text-wrap mb-0" style="font-size: 0.95rem;">
                            {{ item.title }}
                        </p>
                    </div>
                </div>

                <div v-if="!selectTop().length" class="loading">Loading...</div>
            </div>

            <!-- Panel Deskripsi -->
            <div v-if="selectedProduct" class="p-4 rounded-4"
                style="background-color: #E8E8E8; width: 300px; height: 330px;">
                <h6 class="fw-bold mb-3">Description Product</h6>
                <p class="small mb-3" style="text-align: justify;">
                    {{ selectedProduct.description }}
                </p>

                <p class="small mb-1">
                    <strong>Stock:</strong> {{ selectedProduct.rating.count }} pcs
                </p>
                <p class="small mb-1">
                    <strong>Rate:</strong> {{ selectedProduct.rating.rate }}/5
                </p>
                <p class="small mb-3">
                    <strong>Harga:</strong> ${{ selectedProduct.price }}
                </p>

                <button class="btn btn-outline-dark btn-sm rounded-pill px-4">
                    Checkout
                </button>
            </div>

            <!-- Panel default -->
            <div v-else class="p-4 rounded-4 d-flex align-items-center justify-content-center text-center text-muted"
                style="background-color: #E8E8E8; width: 300px; height: 330px;">
                <p class="small mb-0">Click katalog card to know more</p>
            </div>
        </div>
    </div>
</template>

<script>
import axios from "axios";

export default {
    name: "ProductCard",
    data() {
        return {
            jeweleryProducts: [],
            selectedProduct: null,
            bgColors: ["#94A197", "#A39E98", "#D1BEB4"],
        };
    },
    methods: {
        async getProducts() {
            try {
                const res = await axios.get("https://fakestoreapi.com/products/");
                const all = res.data;
                this.jeweleryProducts = all.filter((p) => p.category === "jewelery");
            } catch (error) {
                console.error("Gagal mengambil data:", error);
            }
        },
        selectTop() {
            if (!this.jeweleryProducts.length) return [];
            return this.jeweleryProducts
                .sort((a, b) => b.rating.rate - a.rating.rate)
                .slice(0, 3);
        },
    },
    mounted() {
        this.getProducts();
    },
};
</script>

<style scoped>
.rounded-bottom-4 {
    border-bottom-left-radius: 1rem !important;
    border-bottom-right-radius: 1rem !important;
}

.loading {
    font-style: italic;
    color: #888;
    margin-top: 20px;
}

div:hover {
    transform: translateY(-3px);
}
</style>
