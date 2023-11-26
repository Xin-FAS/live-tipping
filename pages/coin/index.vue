<script>
export default {
    name: "index",
    data () {
        return {
            list: [
                {
                    coin: 10,
                    price: 10
                },
                {
                    coin: 20,
                    price: 20
                },
                {
                    coin: 30,
                    price: 30
                },
                {
                    coin: 50,
                    price: 50
                },
                {
                    coin: 100,
                    price: 100
                },
                {
                    price: 0
                }
            ],
            activeIndex: 0,
            price: 0
        }
    },
    mounted() {
        this.price = this.list[this.activeIndex].price
    },
    methods: {
        openDialog () {
            this.$refs.popup.open()
        },
        closeDialog () {
            this.$refs.popup.close()
        },
        confirmDialog (value) {
            if (value > 0) {
                this.price = value
                this.activeIndex = ''
            } else {
                uni.showToast({
                    title: '金额不能为空！',
                    icon: 'error'
                })
            }
            this.$refs.popup.close()
        }
    }
}
</script>

<template>
    <view class="p-3 border-top border-light-secondary">
        <view class="rounded py-4 flex flex-column align-center justify-center bg-main">
            <text class="text-white font-sm mb-2">当前金币</text>
            <text class="text-white font-weight-bold" style="font-size: 60rpx;">500</text>
        </view>
        <view class="border-top border-light-secondary my-3"></view>
        <view>
            <text class="font-sm text-secondary">请选择要充值的金币数量：</text>
        </view>
        <view class="flex flex-wrap" style="margin-left: -20rpx;margin-right: -20rpx;">
            <view class="p-2" style="width: 33.3%;box-sizing: border-box" v-for="(item, index) in list" :key="item">
                <view @click="activeIndex = index;price = item.price" v-if="item.price" :class="activeIndex === index ? 'border-main': ''" class="border rounded flex flex-column justify-center align-center" style="height: 130rpx;">
                    <view class="flex align-center">
                        <text style="font-family: 'iconfont'" class="text-warning">&#xe6cf;</text>
                        <text class="font-md font-weight-bold">{{ item.coin }}</text>
                    </view>
                    <text class="font text-light-muted">￥{{ item.price }}</text>
                </view>
                <view v-else @click="openDialog" class="border rounded flex flex-column justify-center align-center" style="height: 130rpx;">
                    <text class="font text-light-muted">自定义</text>
                </view>
            </view>
        </view>
        <view class="position-fixed left-0 bottom-0 right-0 border-top flex px-3 align-center" style="height: 100rpx;">
            <view class="flex align-center">
                <text style="font-family: 'iconfont'" class="text-warning">&#xe6cf;</text>
                <text class="font-md font-weight-bold">{{ price }}</text>
            </view>
            <view class="bg-main rounded flex justify-center align-center ml-auto" style="width: 150rpx;height: 70rpx;">
                <text class="font text-white font-md">去充值</text>
            </view>
        </view>
    <!--    自定义输入框-->
        <uni-popup ref="popup" type="dialog">
            <uni-popup-dialog mode="input" message="成功消息" :duration="2000" before-close @close="closeDialog" @confirm="confirmDialog">

            </uni-popup-dialog>
        </uni-popup>
    </view>
</template>

<style lang="scss">

</style>
