<template>
  <div class="modal-wrap" v-if="상세페이지모달상태 == true">
    <div class="modal">
        <h3>
            {{ 판매상품데이터[선택상품idx].title }}
        </h3>

        <div class="room-img-box">
            <img :src="판매상품데이터[선택상품idx].image" :alt="판매상품데이터[선택상품idx].content" />
        </div>

        <div class="room-info-box">
            <p>
                {{ 판매상품데이터[선택상품idx].content }}
            </p>

            <strong>
                {{ 판매상품데이터[선택상품idx].price / month }} 원
            </strong>
        </div>
        <div class="pay-input-wrap">
            <!-- <input type="text" v-model.trim="month" maxlength="2"/> -->
            <select name="" id="" v-model="month">
                <option v-for="(pay,i) in 12" :key="i" :value="i + 1">
                    {{ `${i + 1}개월(무이자)` }}
                </option>
            </select>
            <p>
                {{ month }} 개월 할부
            </p>
        </div>
        <button type="button" @click="closeModal">
            닫기
        </button>
    </div>
  </div>
</template>

<script>
export default {
    name: "ProductModal",
    data() {
        return {
            month: 1,
        }
    },
    props: {
        판매상품데이터: Array,
        선택상품idx: Number,
        상세페이지모달상태: Boolean,
    },
    watch: {
        month(a) {
            if(a > 12) {
                alert('최대 12개월까지 할부가 가능합니다.');
                this.month = "";
                return false;
            }

            if(isNaN(a) == true) {
                alert('숫자만 입력이 가능합니다.');
                this.month = "";
                return false;
            }
        },
    },
    methods: {
        closeModal() {
            this.$emit('closeModal');
        },
    }
}
</script>

<style>
    .modal-wrap {
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background: rgba(0, 0, 0, 0.5);
    }

    .modal-wrap .modal {
        background: #fff;
        border-radius: 20px;
        width: 100%;
        max-width: 600px;
        padding: 25px 15px;
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
    }

    .modal-wrap .modal h3 {
        margin-bottom: 30px;
    }

    .modal-wrap .modal input,
    .modal-wrap .modal select {
        border: 1px solid #000;
        padding: 10px 5px;
    }

    .pay-input-wrap {
        margin-bottom: 10px;
    }

    .room-info-box {
        margin-bottom: 20px;
    }

    .room-info-box p {
        margin-bottom: 15px;
    }
</style>