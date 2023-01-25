<template>
    <div class="discount-banner">
        <h2>지금 구매하면 50% 할인</h2>
    </div>
</template>

<script>
export default {
    name: "DiscountBanner",
}
</script>

<style>
    .discount-banner {
        display: flex;
        justify-content: center;
        align-items: center;
        height: 200px;
        background: #f5f5f5;
        max-width: 80%;
        margin: 0 auto;
        border-radius: 20px;
        margin-bottom: 50px;
    }
</style>