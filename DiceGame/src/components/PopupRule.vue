<template>
    <div class="wrapper-popup" v-bind:class="getClassPopup">
        <div class="rule">
            <h3>Luật chơi</h3>
            <p>

                Luật chơi xúc xắc hai viên
                Số lượng người chơi: 2 người

                Dụng cụ: 2 viên xúc xắc, bảng ghi điểm

                Cách chơi:
                Tung xúc xắc:
                Mỗi người chơi tung 2 viên xúc xắc vào lượt của mình.
                Cộng tổng điểm của hai mặt ngửa lên.
                Xử lý kết quả:
                Trúng số 1:
                Mất lượt chơi.
                Mất tất cả điểm chưa lưu trong ô điểm hiện tại.
                Chuyển lượt sang người chơi tiếp theo.
                Không trúng số 1:
                Lưu điểm:
                Chọn lưu tổng điểm vừa tung được vào ô điểm hiện tại.
                Đi tiếp lượt chơi bằng cách tung xúc xắc tiếp theo.
                Chơi tiếp:
                Cộng thêm tổng điểm vừa tung vào điểm số đã lưu trong ô điểm hiện tại (nếu có).
                Tiếp tục tung xúc xắc cho đến khi chọn lưu điểm hoặc trúng số 1.
                Kết thúc trò chơi:
                Trò chơi kết thúc khi có một người chơi đạt được số điểm yêu cầu trước.
                Người chơi có số điểm cao nhất khi kết thúc trò chơi sẽ là người chiến thắng.
                
            </p>
            <button v-on:click="confirm" class="confirm">Đã hiểu</button>
        </div>
    </div>
</template>

<script>
export default {
    name: 'popup-rule',
    props: {
        isOpenPopup: { type: Boolean, default: false }
    },
    data() {
        return {

        }
    },
    methods: {
        confirm() {
            console.log('confirm PopupRule.vue');
            this.$emit('handleConfirm')
        }
    },
    computed: {
        getClassPopup: function () {
            return {
                'open-popup': this.isOpenPopup
            }
        }
    }
}
</script>

<style>
.wrapper-popup {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background-color: rgba(0, 0, 0, 0.4);
    opacity: 0;
    visibility: hidden;
    transition: all .3s ease;
}

.wrapper-popup.open-popup {
    opacity: 1;
    visibility: visible;
}

.rule {
    width: 350px;
    padding: 20px;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%) scale(1.2);
    background-color: #fff;
    position: absolute;
    font-family: Arial, Helvetica, sans-serif;
    transition: all .3s ease;
}

.open-popup .rule {
    transform: translate(-50%, -50%) scale(1);
}

/* scale -> class */
.rule h3 {
    margin-bottom: 10px;
}

.rule .confirm {
    cursor: pointer;
    margin-top: 20px;
    padding: 8px 15px;
    border: 2px solid #333;
    background-color: #fff;
    transition: all .3s ease;
}

.rule .confirm:hover {
    color: #fff;
    background-color: #333;
}

/* kết hợp CSS3 với VueJs để xây dựng hiệu ứng - Zoom in - Zoom out */
</style>
