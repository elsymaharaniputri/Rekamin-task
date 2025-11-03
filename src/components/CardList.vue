<template>
    <div class="container my-5">
        <ProductCollection title="Woman Collection" :products="womanProducts"
            sideImage="../assets/images/model-cwo.png" />

        <ProductCollection title="Man Collection" :products="manProducts" sideImage="../assets/images/model-cw.png" />
    </div>
</template>

<script>
import axios from "axios";
import ProductCollection from "@/components/ProductCollection.vue";

export default {
    name: "HomePage",
    components: { ProductCollection },
    data() {
        return {
            allProducts: [],
            womanProducts: [],
            manProducts: [],
        };
    },
    async mounted() {
        try {
            const res = await axios.get("https://fakestoreapi.com/products");
            this.allProducts = res.data;

            // Filter data: jewelry = woman, men clothing = man
            this.womanProducts = this.allProducts.filter(
                (p) => p.category === "jewelery"
            );
            this.manProducts = this.allProducts.filter(
                (p) => p.category === "men's clothing"
            );
        } catch (err) {
            console.error("Gagal ambil data:", err);
        }
    },
};
</script>
