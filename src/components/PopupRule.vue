<template>
    <div class="wrapper-popup" v-bind:class="getClassPopup">
        <div class="rule">
            <h3>Luật chơi</h3>
            <p>Khi người chơi tung xuc xắc đỗ được điểm và cộng dồn các lượt kế tiếp cho tới khi người chơi bấm vào nút lấy điểm. Người chơi nào lấy được số điểm bằng hoặc lớn hơn số điểm đã được quy định trước sẽ thắng. </p>
            <p>LƯU Ý: người chơi sẽ được chọn mục tiêu điểm mà mình muốn chơi vào ô mục tiêu </p>
            <p>Nếu người chơi đỗ xúc xắc vào nút 1 của một trong hai con xúc xắc sẽ bị mất lượt. Lược chơi sẽ trả lại cho đối phương.</p>
            <button 
                v-on:click="confirm"
                class="confirm">Đã hiểu</button>
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
            // Truyền event ra App.vue
            console.log('confirm PopupRule.vue');
            this.$emit('handleConfirm')
        }
    },
    computed: {
        getClassPopup: function() {
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
        background-color: rgba(0,0,0,0.4);
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
