<template>
    <div class="block" v-if="showBlock" @click="stopTimer">
        Click Me!
    </div>
</template>

<script>
export default {
    props: ['delay'],
    emits: ['end'],
    data() {
        return {
            showBlock: false,
            timer: null,
            reactionTimer: 0
        }
    },
    mounted() {
        setTimeout(() => {
            this.showBlock = true
            this.startTimer()
        }, this.delay)
    },
    methods: {
        startTimer() {
            this.timer = setInterval(() => {
                this.reactionTimer += 10
            }, 10)
        },
        stopTimer() {
            clearInterval(this.timer)
            this.$emit('end', this.reactionTimer)
            console.log(this.reactionTimer)

        }
    }
}
</script>

<style>
.block {
    width: 400px;
    border-radius: 20px;
    background: #0faf87;
    color: white;
    text-align: center;
    padding: 100px 0;
    margin: 40px auto;
}
</style>