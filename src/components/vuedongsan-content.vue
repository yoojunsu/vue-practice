<template>
    <div class="room">
        <div class="room-img-box">
            <img :src="판매상품데이터.image" alt="">
        </div>
        <div class="room-info-box">
            <h3 @click="detailModalOpen">
                {{ 판매상품데이터.title }}
            </h3>
            <strong>
                {{ 판매상품데이터.price }}
            </strong>
        </div>
        <div class="report-btn-box">
            <button type="button" @click="report">
                허위매물신고
            </button>
            <span>총 신고수: {{ 신고수 }}</span>
        </div>
    </div>
</template>

<script>
export default {
    name: "VuedongsanContent",
    data() {
        return {
            신고수: 0,
        }
    },
    props: {
        판매상품데이터: Object,
    },
    methods: {
        detailModalOpen() {
            this.$emit('openModal', this.판매상품데이터.id);
        },
        report() {
            this.신고수 += 1;
        }
    }
}
</script>

<style>

.room-cont-wrap .room-info-box h3 {
    margin-bottom: 20px;
    cursor: pointer;
}
</style>